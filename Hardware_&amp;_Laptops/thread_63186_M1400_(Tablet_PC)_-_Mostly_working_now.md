---
title: "M1400 (Tablet PC) - Mostly working now"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by TabletGuy on 2005-09-07
Hi all

I've been an Ubuntu user for fours days now. Just wanted to post a note to say I have managed to get the following working under Hoary.

Hi all

I wanted to share that I now have my m1400 working with Linux (and actually like it better than Windows Tablet Pc edition - the system is much faster).

Here's my setup:
Os: Duel booting Ubuntu Linux and Windows XP. Ubuntu resized my Windows NTFS disk partition and added a new linux and swap file partion.

Hardware:
Pen - works fine (had to apt-get (download) one utility - setserial) and copy and paste changes into xorg.conf file.

USB keyboard, mice, digital camera - all work fine out of the box.

Onscreen keyboard: Had to download and install GOK and one additional file, again no problems. I like this more than the Windows on screen keyboard.

Handwriting, etc - in two years of tablet pc use I haven't enjoyed the MS Handwriting tools so I don't miss these.

Journal - Gnournal works fine (but isn't as pretty).

Suspend and Hibinate - work fine, had to manually edit my GRUP menu.lst file.

Screen brightness: Works fine - at the moment I have to adjust this via the command line - but I think there is an app called Tabitha which will do this for me (kinda like Dashboard for Linux).

Wireless net connection: Works fine out of the box. Just had to learn how to disable and enable network adapters in Gnome instead of windows :)

What's missing:
Easily do handing writing markup on docs and emails (like in Office 2003).

Good ebook reader like Ubook (I think I will write this myself). 

Haven't yet got the screen rotation and the four buttons on the side working.

If anyone needs specifics on how to set it all up let me know.

If I can get the screen rotation working I'm not going back

I've also cross posted this to TabletPcBuzz.com.

I'm quite pleased with myself :) nearly there!

---

### Post by chovija on 2005-11-16
Hi tablet Guy.:) 
I have a Lenovo X41 Tablet PC, and has just installed Breeze on it..
But the main Issue is that i have not be able to enable the Pen in Breeze..
I agre with you that that system is much faster that Windows Tablet PC..
I have found some info about the hardware that uses my Tablet PC, and y need to enable the serial por using setserial command, but i do not found a place to put the setserial command during startup (like rc.d in fedora).
Any Help would be realy apreciated..

Chovija.!:cool:

---

### Post by reidarma on 2005-12-22
Hi. I am trying to make the pen work as well for my X41 tablet. 
I ran setserial* /dev/ttyS0 port 0x0200 irq 5 autoconfig* and * wacdump -f c100 /dev/ttyS0* to test the pen. This works fine in other distros as mandriva and fedora. 
But I keep getting *WacomOpenTablet: Invalid argument* in Ubuntu. Im happy to hear if anyone has made stylus working in Ubuntu for X41.

Thanks in advance

---

### Post by reidarma on 2005-12-22
Ok. I managed to make stylus working on may IBM X41 on Ubuntu.
I have messed around with some configs, but the importaint thing is that the stylus was on */dev/ttyS14* and not */dev/ttyS0*.
My xorg.conf has this essential settings:
> 
....
....
 Section "InputDevice"
       Driver        "wacom"
       Identifier    "cursor"
       Option        "Device"        "/dev/ttyS14"
       Option        "Type"          "cursor"
       Option        "ForceDevice"   "ISDV4"
       Option        "Mode"          "Absolute"
  Option        "Button3"        "2"
       Option        "Button2"        "3"
       Option        "TPCButton"     "on"
 EndSection

 Section "InputDevice"
       Driver        "wacom"
       Identifier    "stylus"
       Option        "Device"        "/dev/ttyS14"
       Option        "Type"          "stylus"
       Option        "ForceDevice"   "ISDV4"
 EndSection

.....

.....
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "stylus" "SendCoreEvents"
EndSection



And I am loading these modules: in */ets/modules*
> 
wacom
wacom_acpi


No need for the setserial-stuff in my case. 

Hope this info helps :)

---

### Post by one_stinky_bum on 2006-08-15
Anyone noticed information for people with Finepoint digitizers? Can't get the digitizer/pen to work properly on my Gateway M280

---

### Post by one_stinky_bum on 2006-08-18
I found out from Wikipedia that it (M280, CX200/210, CX2600/2700 etc) uses the Finepoint MP-800 digitizer. Hopefully this would help if someone can be of assistance.

---

### Post by alexvd on 2006-08-23
Hello I am trying to install 6.06 onto a Motion m1400 as well. I am trying to install via an external firewire Acer (rebadged Aopen) Dvd/cd drive. The motion tablet has 504megs of memory. 

Currently I have windows beta2 5384 installed but it is really really slow so I want to change. Aside from that I really want to run linux so that I can put a mythfrontend on it.   

So I burned the iso to cd-rw media 8x. When i boot from the It loads the initial splash screen. I can run a disc check. This comes out clean.  After I select the option for install.  It runs through install checks, then goes to hardware drivers.  It hangs here sending irq11 message.  disables irq11.  After this it tries to load ieee1394:spb2: aborting sbp2 command.  reset the request and then aborts the sbp2.  It then rattles off a ton of errors.  sr 0:0:0:0: rejecting  I/O to offline device.  [fail]

I cant figure out what I am doing wrong.

---

### Post by alexvd on 2006-08-23
Hello I am trying to install 6.06 onto a Motion m1400 as well. I am trying to install via an external firewire Acer (rebadged Aopen) Dvd/cd drive. The motion tablet has 504megs of memory. 

Currently I have windows beta2 5384 installed but it is really really slow so I want to change. Aside from that I really want to run linux so that I can put a mythfrontend on it.   

So I burned the iso to cd-rw media 8x. When i boot from the It loads the initial splash screen. I can run a disc check. This comes out clean.  After I select the option for install.  It runs through install checks, then goes to hardware drivers.  It hangs here sending irq11 message.  disables irq11.  After this it tries to load ieee1394:spb2: aborting sbp2 command.  reset the request and then aborts the sbp2.  It then rattles off a ton of errors.  sr 0:0:0:0: rejecting  I/O to offline device.  [fail]

I cant figure out what I am doing wrong.

---

### Post by alexvd on 2006-08-25
Hi I fixed this with irqpoll option very cool.

---

### Post by kderose on 2006-08-30
I've been trying to get my stylus working on my ibm x41 tablet...I'd appreciate any help from you experts :-)

I have my xorg.conf file edited with the device being /dev/ttyS4 as assigned by the device manager, and this works on booting up and restarting, but when I suspend and restore it stops working.  The setserial command is also not working...I just get a message saying the driver or device is busy.  Any suggestions????

Thanks!!

-Kim

---

### Post by TabletGuy on 2006-08-31
Sorry can't help with the suspend option. When I used breezy I couldn'y get the system to reliably enter suspend or hibinate and gave up.

I just installed dapper on the M1400 using an external Sony CD. Live CD booted fine and the system installed fine.

Only change necessary was to change the xorg.conf file to the correct serial port, ie change:
/dev/wacom
to
/dev/ttyS4

this might help anyone else setting up their M1400.

---

### Post by TabletGuy on 2006-08-31
Also had to add the line:
Option        "Button2"       "3"

to make the pen button work as a right mouse button on the M1400.

Complete stylus input should read:
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS4"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "Button2"       "3"
EndSection

---

### Post by LyubinVadim on 2006-09-04
I want to buy a new Lenovo ThinkPad X41 Tablet 1866 Pentium M 758 1.5 GHz LV Centrino RAM : 512 MB HD : 60 GB Gigabit Ether 18663RU from [here](http://search.stores.ebay.com/Costupdate_tablet-pc_Laptops-Notebooks_W0QQcatrefZC12QQfcdZ2QQfciZ4QQfclZ4QQfcpgZ20QQfhpgZ21QQfromZR10QQfsnZCostupdateQQfsooZ2QQfsopZ2QQftsZ2QQrefidZstoreQQsacatZ51148QQsaselZ3743435QQsbrsrtZdQQsofpZ0) on costupdate store on eBay.
[IMG]http://thumbs.ebaystatic.com/pict/320018931645_0.jpg[/IMG]
What do you think about this choice?... I often work with graphics.:confused:

---

### Post by alexvd on 2006-10-13
tablet guy.

do you have bluetooth on your m1400? Is it working.  

Also did you get the fingerprint reader working.  I really want to be able to enter passwords for login and web this way.  

Did you ever install tabitha to assign the buttons if so how is this working.

---

### Post by TabletGuy on 2007-05-17
> **alexvd said:**
> tablet guy.

do you have bluetooth on your m1400? Is it working.  

Also did you get the fingerprint reader working.  I really want to be able to enter passwords for login and web this way.  

Did you ever install tabitha to assign the buttons if so how is this working.

Thought I would resurrect this thread because several people have PMed me saying they are looking at putting Ubuntu on a M1400.

The only thing I don't have working now are:
1. The fingerprint reader - mine is broken now.
2. A good launcher programme.
3. Hibernation.

I don't use bluetooth so can't say how good this is.

I am using avant-windows-manager as my launcher which is ok but what I want is a launcher I can bind to a start up key.

I found this thread useful for little things:
[http://forums.murc.ws/showthread.php?p=625380](http://forums.murc.ws/showthread.php?p=625380)

This guy show you how to bind to screen rotation and side button binding working.

I use OnBoard as my keyboard- works really well.

What I really want is to be able to install a copy of Windows TPC edition as a virtual machine so I can use one note seamlessly. Any one know how to do this - my OEM Motion Computing Tablet PC CD won't install as a VM.

If I have some time I guess I will try to install it as a normal hardware install and convert it using the VMware conversion tools but if someone knows an easier way please post it. It would be good to have the option of using the windows TPC features if necessary.

---

### Post by jharbert on 2007-05-19
My tablet (Toshiba Portege M205) has been workin quite nicely with Ubuntu.  I put together a [guide]("http://ubuntuforums.org/showthread.php?t=371510") from various sources if anyone is interested.  As for a notetaking app, I would recommend Xournal.  It allows for marking up PDF files.

---

### Post by alexvd on 2007-05-21
Hi tablet pc guy thanks for responding.  I am still using the motion tablet pc m1400.  

I can't seem to get the stylus working since my upgrade to fiesty.  Can you post you instructions on how you have it working now.

I tried using GOK for keyboard.   It was quite poor, frankly Vista is really really good.   I hope that onboard works better. 

If anyone can get the biometric fingerprint working please let me know.

---

### Post by TabletGuy on 2007-05-25
Alex,

The pen on M1400 worked out of the box  on a clean install of Feisty. I would suggest a fresh install which should solve the problem.

If you don't want to do this there could be lots of things getting in the way - can you use the pen at all or is there no pen input whatsoever?

I couldn't get GOK to function well but onboard works fine for me .

Sorry I don't use the finger print reader.

---

### Post by alexvd on 2007-06-29
Hi can you post your xorg for me

---

