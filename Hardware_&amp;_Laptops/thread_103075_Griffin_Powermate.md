---
title: "Griffin Powermate"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by phosphoricx on 2005-12-13
Can anybody point me to a guide on how to install drivers for a [Griffin Powermate]("http://www.griffintechnology.com/products/powermate/")? I found [some info]("http://www.eviloverlord.net/powermate.html") via Google, but it talks about patching a 2.4 kernel and I'm using 2.6 with Ubuntu, plus I don't want to lose support once I upgrade the kernel.  How can I get my Powermate to play nicely?

---

### Post by theToolman on 2006-03-06
Hey I am also trying to get it to go.  The kernel has the module by default in ubuntu, but I think hotplug/UDEV need to be configured.. I have got a new device to show (/dev/powermate) by following this page, but not all of it is applicable:

[http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x](http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x)

I don't know much about this so Im still fumbling around.  Also; I am planning to use gizmod, though it doesn't want to compile for me.  I think i is relying on x86 so xorg X11 isn't working.  I'll post any more details if I suss anything...

---

### Post by theToolman on 2006-03-07
I have got it going!  Im using kubuntu breezy std. 2.6.12-10-k7 if anyone is interested.

I'll document it now:

**Step 1: get it showing in /dev/  **
I have little knowledge about hotplug and UDEV: if you can't find information on the links below, I can't answer your questions about these.  That said, the following links helped me get it to show up.  Indeed this is pretty much a pick n mix from these 2 pages - thanks whoever authored them.  Suggestions for improvement welcomed.

[http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x]("http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x")
[http://www.qsl.net/n0nb/linux/debianhotplug.html]("http://www.qsl.net/n0nb/linux/debianhotplug.html")

Firstly; create the file: /etc/hotplug/usb/powermate.usermap, you will need to be root to write this file. 

   you@home $ sudo nano  /etc/hotplug/usb/powermate.usermap

next put the following 2 lines in the file and save (ctrl-x, 'y'es to save)

# usb module	match_flags	idVendor	idProduct	bcdDevice_lo	bcdDevice_hi	bDeviceClass	bDeviceSubClass	bDeviceProtocol	bInterfaceClass bInterfaceSubClass	bInterfaceProtocol	driver_info
powermate      0x0003 0x077d   0x0410    0x0000       0x0000       0x00         0x00          0x00            0x00            0x00            0x00            0x00000000


I included the legend incase you were interested.  Looks like its just referencing the vendor and product ID.  Nothing exciting here.  Next, create the file: /etc/hotplug/usb/powermate, again you will need to be root to write this file. 

   you@home $ sudo nano  /etc/hotplug/usb/powermate

next put the following lines all the way to the #end in the file, and save (ctrl-x, 'y'es to save)

#!/bin/bash

LOGFILE="/var/log/powermate"

time=`date +"%b %d %X"`
uname=`uname -n`

echo "$time $uname $0: Griffin PowerMate Detected" >> $LOGFILE

/sbin/rmmod evdev powermate
/bin/sleep 1
/sbin/modprobe powermate
/bin/sleep 1
/sbin/modprobe evdev

echo "$time $uname $0: Griffin PowerMate Loaded" >> $LOGFILE
#end

Yep that is the end of the file there! You can change the log file if you prefer logging elsewhere. Now you'll need to set the executable flag on this script.

   you@home $ sudo chmod +x  /etc/hotplug/usb/powermate

OK this is the end of the hotplug setup.  Now we need to setup UDEV. As I understand it, UDEV is the tool that 'creates' the /dev/powermate device we are trying to setup.  What I do here works but might not be perfect.

disclaimer aside; The Gentoo page shows 2 alternate ways of setting up UDEV but has something not clear to me - it suggests "Since the rules are sorted alphanumerically, make sure the name is beyond the standard 50-udev.rules:" and the next line defines the file name as "File: /etc/udev/rules.d/45-powermate.rules" ...

I dont think the ambiguity affects ubuntu - it doesnt have other files with numbers.  In any case, I'll use 75 as my prefix for safe measure.

so... create the file: /etc/udev/rules.d/75-powermate.rules, again you will need to be root to write this file. 

   you@home $ sudo nano  /etc/udev/rules.d/75-powermate.rules

And put the following line in the file and save (ctrl-x, 'y'es to save).

BUS="usb", KERNEL="event*", SYSFS{product}="Griffin PowerMate", SYMLINK="powermate"

Neither locations exist for the second file shown in both alternates (gentoo page).  Leaving it out works fine for me at least.  So.. lets restart hotplug then run udevstart.  Warning: udevstart messes my sound card audio levels and mute settings - noisey! 

you@home $ sudo /etc/init.d/hotplug restart
you@home $ sudo udevstart

at this point you should plugin or re-plugin your powermate.  if all goes well, dmesg should show the device registration...


you@home $ dmesg
...
[4559214.447000] usb 3-1: USB disconnect, address 2
[4559217.554000] usb 3-1: new low speed USB device using uhci_hcd and address 3
[4559217.698000] usbhid: probe of 3-1:1.0 failed with error -5
[4559217.706000] input: Griffin PowerMate on usb-0000:00:10.2-1/input0
[4559218.192000] usbcore: deregistering driver powermate
[4559219.315000] input: Griffin PowerMate on usb-0000:00:10.2-1/input0
[4559219.315000] usbcore: registered new driver powermate
...

and you should have the device /dev/powermate:

you@home $ ls /dev/powermate
/dev/powermate
you@home $ echo w00t it works

hope that last command worked ;)  ok so now you need to install some tool to 'listen' and react.  I have owned my powerball for 6 hours now, but my educated opinion is that [gizmod]("http://gizmod.sourceforge.net/") is the tool for that.  


First get all these libraries:

you@home:~ $sudo apt-get install \
alsa-source \
libasound2-dev \
libxosd2 \
libxosd-dev \
build-essential \
libxxf86vm-dev\
 \
xmms \ 
xmms-dev \

the last 2 can be omitted by adding --enable-xmms=no to the ./configure later on.
<still compiling> 
So lets get the file (version Im using [from this link]("http://prdownloads.sourceforge.net/gizmod/gizmod-2.1.tar.bz2?download")) and save it to your home folder, then unpack it.  feel free to change the paths appropriately if you know how :D

you@home: ~ $echo file downloaded to here, the home folder isnt it!
you@home:~ $ tar xjf gizmod-2.1.tar.bz2
you@home:~ $ cd gizmod-2.1
you@home:~/gizmod-2.1 $./configure
you@home:~/gizmod-2.1 $make
you@home:~/gizmod-2.1 $sudo make install

From here you can go look at how to tweak the config file on the gizmo
hopefully that should work.  If not, try and figure out which dependancy is missing and I can add to list.  


It has some dependcies that the configure script doesnt find.  For that reason, sorry if i have missed a dependancy that I missed on the list. 



<in progress..saving..>

---

### Post by jmcts on 2007-02-07
I have tried to get my powermate working under edgy eft but there is no etc/hotplug folder.  Can you help with that?

---

### Post by mattmac24 on 2007-05-06
> **jmcts said:**
> I have tried to get my powermate working under edgy eft but there is no etc/hotplug folder.  Can you help with that?

same problem. has anybody got this working on fiesty fawn? ive tried a few guides with no success

thanks,

Matt:)

---

### Post by BrNBrN on 2007-08-05
I have same problem :) 

I think, we must create hotplug folder but I dont know how to create.

I will use powermate with ubuntu studio. My kernel version is 2.6.20-16-lowlatency.

can anybody help me?

---

