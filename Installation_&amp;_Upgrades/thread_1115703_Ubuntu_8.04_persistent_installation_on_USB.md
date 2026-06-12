---
title: "Ubuntu 8.04 persistent installation on USB"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by bobbypavan on 2009-04-04
hi all
I installed ubuntu 8.04 LTS persistent on to my 4GB USB pendrive and after making some changes to syslinux configuration file            I made it run in LIVE user mode. GUI is turning up and working smoothly. But when I try persistent mode it is going to command line interface directly and no GUI is turning up.

How to fix this problem.. 

In LIVE user mode (using a LIVE CD and mounting this USB), i tried editing the initrd file in casper folder using gedit. But it is saying there is no space left to write the edited file to the USB..
but the USB except for the system files is totally free.

What should i do..

---

### Post by dandnsmith on 2009-04-04
> **bobbypavan said:**
> hi all
I installed ubuntu 8.04 LTS persistent on to my 4GB USB pendrive and after making some changes to syslinux configuration file            I made it run in LIVE user mode. GUI is turning up and working smoothly. But when I try persistent mode it is going to command line interface directly and no GUI is turning up.

I suggest that you try to pass something like vga=xxx to the ubuntu kernel (if it would normally be expected to give the GUI interface) or force some grahics like (but depends on your hardware) xforcevesa. Note, I don't have the 3 digit codes for the vaious modes for vga to hand, so you'll need to delve for them.

> In LIVE user mode (using a LIVE CD and mounting this USB), i tried editing the initrd file in casper folder using gedit. But it is saying there is no space left to write the edited file to the USB..
but the USB except for the system files is totally free.

I've found this - it seems to put the whole of the usb filesystem in protected mode, so, at one stage I had to invoke a second usb stick to get in some driver data. The only place which gets written is the area designed for it - the casper-rw file.
What were you hoping to do with initrd changes?

I think it must be a protection, to stop you corrupting the installation, and you may need a second partition to allow writing (no idea whether this messes up the usb stick use)

---

### Post by bobbypavan on 2009-04-04
Thank you for the reply..

> **dandnsmith said:**
> I suggest that you try to pass something like vga=xxx to the ubuntu kernel (if it would normally be expected to give the GUI interface) or force some grahics like
xforcevesa.

Being a beginner I don't know how to force the kernel to use 'vga' thing.  Can you please give me some more info for proceeding further.

Coming to initrd file, I was trying to remove mode=755 in the following line

"mount ${cowdevice} -t ${cow_fstype} -o rw,noatime,mode=755 /cow".

Somewhere on web i read that it is a glitch with 8.04 and it can be solved by doing this change. But i couldn't go that far.

---

### Post by dandnsmith on 2009-04-05
Are you by any chance using the stuff from [here](http://www.pendrivelinux.com/how-to-fix-ubuntu-804-casper-script-for-persistence/) ?
If so, you don't seem to be following the script properly - you're supposed to be running the liveCD to get to do the edit, and then write the new initrd to the usb  **without running ubuntu from it**

For the other matter, you need to read up how to pass parameters to the kernel at boot time from the kernel line in the menu

---

### Post by bobbypavan on 2009-04-06
yeah I realized that some time later and edited the initrd.gz file, zipped it and saved it in the same place using Live CD. 

but this time it is giving some other error to the tune of kernel image not in sync.. :lolflag:

I don't know what all were happening with that. I got irritated with 8.04 and formatted the pen-drive. Now installed 8.10, and this time syslinux.cfg file is kind of empty. There is no code which points to kernel or initrd.gz files

Any way thanks for the help man :)

---

