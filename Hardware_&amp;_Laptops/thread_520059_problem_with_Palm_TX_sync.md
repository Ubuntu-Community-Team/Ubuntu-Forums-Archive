---
title: "problem with Palm TX sync"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Elf on horseback on 2007-08-07
I am trying to get my Palm TX to sync with my PC.  The hand held will beep when I plug in the USB sync cable but that's it.  

I have tried J Pilot, K Pilot.  Then I tried configuring Gnome-Pilot, and retrying Jpilot and Kpilot.  still nothing.  Every post I was able to find was all this complex stuff in the Terminal, then again everything at the command line is confusing to me.  I tried Google too samething.

Any help will be most welcome, thank you

---

### Post by Elf on horseback on 2007-08-07
never mind i figured out part of it, thank you tho

---

### Post by Venefyxatu on 2007-08-15
Hi,

Would you mind posting the parts you figured out?  I'm trying to get my own TX to sync, but I'm also having trouble .. perhaps you figured out that one step I missed ;)

---

### Post by Elf on horseback on 2007-08-16
> **Venefyxatu said:**
> Hi,

Would you mind posting the parts you figured out?  I'm trying to get my own TX to sync, but I'm also having trouble .. perhaps you figured out that one step I missed ;)

I'll do my best to explain it out NOTE this is sync ing over wi-fi

Ubuntu computer
1. Go in to system>preferences>Palm OS Devices, that will open up gnome-pilot.
2. Click the devices tab
3. Click the button that says New
4. only thing you need to change is where it says type, change it to network
5. click close on that window but keep gnome-pilot open, has to be open for it to work
6. run ifconfig and note your local IP address
(mine is right after Inet addr:)

Palm TX
1. make sure your wi-fi is on
2. on the main menu go to "HotSync"
3. change the sync to network
4. under the HotSync logo there is a drop down menu, on there pick "Select PC"
5. go next
6. when it finds nothing click the "other..." button
7. put in the IP address of you computer
8. click done
9. click the HotSync logo to hot sync and you should sync up with Evolution.  I am still finding out how to change the program it syncs to

Hope it helps
-Elf

---

### Post by Venefyxatu on 2007-08-17
Thanks a lot!  That looks surprisingly easy :)

I managed to get it to sync over the cable with JPilot (and am working on writing down the required steps as well as figuring out the effect of some of them ;) ), just not with gnome-pilot.  As far as I know it syncs with the application that's running and accepts the connection?

---

### Post by Elf on horseback on 2007-08-17
> **Venefyxatu said:**
> Thanks a lot!  That looks surprisingly easy :)

I managed to get it to sync over the cable with JPilot (and am working on writing down the required steps as well as figuring out the effect of some of them ;) ), just not with gnome-pilot.  As far as I know it syncs with the application that's running and accepts the connection?

thank, i've been trying to hry JPilot to work with this thing

As far as i know the only program it syncs with is Gnome-pilot and it redirects the palm to what ever program from there.

---

### Post by Venefyxatu on 2007-08-18
Okay, I think I figured most of it out.  From what I've seen, gnome-pilot is not necessary to synchronize with jpilot (proof being that I cannot setup gnome-pilot due to an error, and I can still sync ;) ).
These steps are what's needed to get it to sync via the USB cable - I'm not sure what needs to be done to get jpilot to talk to your Palm via wireless (and since I don't have a wireless connection I unfortunately can't try to figure it out).  If you're going to use the cable, you can try starting at step 8 - with some luck it'll work from there ;)

A quick disclaimer : I refuse to take responsibility for anything going wrong.  What I'm describing here is what worked for me ... 

And a quick note : I've used Gentoo, but the basic idea should be the same ... (yes, I registered specifically for this thread ;) )

Also : I know it's a lot of command-line; I hope the included examples help making it easy to understand!  Once you learn how to use it, it'll become a lot easier and faster than using the GUI ;)

Any and all feedback and / or questions are welcome (via reply, PM, e-mail or instant messenger)!


**Prerequisites**
[list]
[*]Kernel 2.6 (with specific options, see further)
[*]udev
[*]NPTL
[*]pilot-link (optional? Not sure, but I doubt it)
[*][optional] gnome-pilot
[*][optional] evolution
[*][optional] jpilot
[/list]

**Setting it up**
[LIST=1]
[*]Install the prerequisite software.  (that's cheating, isn't it? ;) ). For specific instructions, I'll need to refer you to the Ubuntu community and/or documentation.
To check for NPTL, you can use 
```
**venefyxatu@necronomicon ~ $** getconf GNU_LIBPTHREAD_VERSION
NPTL 2.5 
```
[*]Connect your Palm to your computer via the USB cable
[*]Run lsusb (this command will show you what USB devices are connected to your computer) and see if any information related to your Palm shows up.  If it doesn't, this might indicate a hardware problem.
```
**venefyxatu@necronomicon ~ $** /usr/sbin/lsusb 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 015: ID 0830:0061 Palm, Inc. 
<snip>
```
[*]Make sure the kernel is compiled with the correct modules.  You can use the next step to check if this is already the case!
The modules can be found under Device Drivers --> USB Support --> USB Serial Converter support
```
Device Drivers --> USB Support --> USB Serial Converter support
	<M>	USB Serial Converter support
	[ * ]		USB Generic Serial Driver
	...
	<M>		USB Handspring Visor / Palm m50x / Sony Clie Driver
```
[*]Try the following command as root.  If you get no output, everything is fine.  If you get the error shown, you don't have the required module, although it might be compiled into the kernel.  Perhaps one of the Ubuntu guru's could clarify whether it's there by default?
```
**necronomicon ~ #** modprobe visor
FATAL: Module visor not found
```
[*]If you want to make sure the modprobe command went okay, use the following command to check : 
```
**venefyxatu@necronomicon ~ $** lsmod | grep visor 
**[COLOR="Red"]visor[/COLOR]**                  17036  0 
usbserial              25704  1 [COLOR="Red"]**visor**[/COLOR] 
```
[*]As root, edit the file 10-udev.rules in the udev rules folder ( /etc/udev/rules.d/ in my case ... if the aforementioned Ubuntu guru is still around, perhaps they can clarify where it's located?).  If it doesn't exist, create it.  Putting the rule in this file ensures that it is executed before the default rules in 50-udev.rules .  It needs the following line : 
[COLOR="Red"]IMPORTANT : This needs to be ONE SINGLE line![/COLOR]
```
BUS=="usb", SYSFS{product}=="Palm Handheld", KERNEL=="ttyUSB[13579]", NAME="pilot", GROUP="usb", MODE="0770"
```
I can't remember where I found this information - as soon as I found it back I'll add it here.  This should be generic enough to work with (any?) Palm, at least with the TX.
[*]Disconnect your Palm, wait a moment, then reconnect it.  If everything's gone well, you should have a /dev/pilot node.  Make sure your user is a member of the group shown for this node!  (in this case "usb"). 
```
**venefyxatu@necronomicon ~ $** ls -lh /dev/pi*

crwxrwx--- 1 root usb 188, 1 Aug 18 14:47 /dev/pilot

```
[*]Open the HotSync application on your Palm, and make sure it is set to synchronize via Cradle/Cable
[*]Press the Synchronize button on your Palm
[*]For testing purposes, as your regular user, run the following command.  When it asks you to press the HotSync button, don't do it (you've just done so, remember? ;) ).  Just wait a moment for the connection to get set up (this shouldn't take more than a few seconds).
```
**venefyxatu@necronomicon ~ $** pilot-xfer --port /dev/pilot -l


   Listening to port: /dev/pilot


   Please press the HotSync button now... Connected
```
You should see a whole list of information scrolling by (252 files in my case).  This means the connection works!
```
Reading list of databases in RAM...
<snip>
List complete. 252 files found.

Time elapsed: 0:00:02


```
[/LIST]

From here, synchronizing with an application like jpilot should be dead simple : 

**Synchronizing**

This is the order that works for me : 
[LIST=1]
[*]Connect the Palm via the cable
[*]On your computer, start the application to synchronize with (e.g. jpilot)
[*]Press the HotSync button on the cable (or in the HotSync application on the Palm)
[*]On your computer, give the application you're using the Synchronize command (in jpilot : the sync button)
[/LIST]

Tah-dahh!

**About the udev rule**

First of all, a great reference if you want to know more about it is this website : [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html).  
What's important is that all the match keys (the ones with two equals signs : "==") combined can uniquely identify your Palm.
The different keys in my example line and what they mean are : 
[LIST]
[*]BUS=="usb"
IF a device is connected on the USB bus
[*]SYSFS{product}="Palm Handheld"
AND this device has a product name "Palm Handheld".  Some people prefer to add a wildcard at the end (like so : "Palm Handheld*"), but this doesn't seem to be necessary.
[*]KERNEL=="ttyUSB[13579]"
AND this device is named ttyUSB1 or ttyUSB2 or ... by the kernel.  For some reason, only the odd numbers seem to work properly!
[*]NAME="pilot"
THEN create a device node named pilot ( this is the /dev/pilot that most syncing applications look for).
[*]GROUP="usb"
The group to assign to the pilot node.  If your user is a member of this group, you will have read / write / execute permissions (set in the next key)
[*]MODE="0770"
This gives 0770 access (-rwxrwx---) permissions to the created node.  0660 (-rw-rw----) should suffice as well, but apparently gnome-pilot is greedy and demands 0770 (-read, write, execute for owner (root), read, write, execute for group (usb), nothing for everyone else)
[/LIST]

---

### Post by Elf on horseback on 2007-08-18
Thanks for posting what to do, its a huge help, Thanks a Mill Venefyxatu.

---

### Post by ShamusPatt on 2007-08-22
The visor stuff is considered obsolete, and it's slow as well. If you can configure it to use libusb you're much better off. 

I had this working fine on my Zire 71 but recently have moved to a T/X as well, and found that it wouldn't work with gnome-pilot. However, I got a tip from another posting somewhere on how to fix it. It seems the T/X is missing from the gnome-pilot configuration file. You can add it in; just put this line somewhere in  /usr/share/gnome-pilot/devices.xml:

<device vendor_id="0830" product_id="0061" />

Restart gpilotd, and you should be good to go syncing over usb. (Just use usb: as your device instead of /dev/ttyUSB1 or whatever you used with Visor).

FYI, I'm running "Feisty".

*** Just an update. 

The <device> entry above is already in devices.xml. The comments indicate that the entry is for "Palm Zire 31, Palm Tungsten E2 and Palm Treo 650" but the device codes are right. I guess I just got lucky when I hot-sync'ed after thinking I'd fixed up the configuration file.

---

### Post by John747 on 2007-08-23
I was able to get my Treo 650 working with Feisty and Jpilot by just running:
             modprobe visor
I tried other things too, but I don't think anything else helped except maybe
installing pilot-link.  :)

---

### Post by ShamusPatt on 2007-08-23
A small update to my note about hacking devices.xml . Upon closer look, the USB ID that I added (0831/0061) is already in the file. The comment reads "Zire 31" but that shouldn't matter.

I'm at a loss as to why USB didn't work before, but now it does (at least some of the time).

---

