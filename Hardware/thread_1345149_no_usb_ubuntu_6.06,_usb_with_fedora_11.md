---
title: "no usb ubuntu 6.06, usb with fedora 11"
date: 2009-12-03
forum: Hardware
---

### Post by linuxnovo on 2009-12-03
I am using an Acer Travelmate 517TE laptop.  It has 366MHZ CPU with 256 RAM and a 4.9 hard drive.  It has one usb port.  I have tried several OS's in this thing.  It seems to run fine with Ubuntu 6.06.  The only significant problem is that it will not detect the usb.

First, I have made sure that the usb was enabled in the Bios.  This is an often overlooked place outside of the OS that will produce this effect.  All is well here.  Not a Bios problem

Second:  The command lsusb produces nothing.  Likewise mtab and fstab have nothing.  Dmesg before and after the plug in of the usb flash drive shows no difference.  I have tried using the mount command.  No effect.

Third:  Last night I used Fedora 11 as a live disk.  Of course, it did not function well.  But, it is a big but, but the usb flash drive mounted automatically and contents displayed.  Clearly, there is no hardware problem here.  It is an OS problem completely.

Question:  What does Fedora 11 have that Ubuntu 6.06 does not?  Anyone got any ideas????

---

### Post by mörgæs on 2009-12-03
How does 6.06 from your live disk behave? 

If everything fails, you could also try a minimal new Ubuntu: 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by linuxnovo on 2009-12-04
It responds the same way that the install does.  I have used for sometime linux mint 4.  It's multimedia was great, but the archives were out of date and performance is quirky.  Still no usb.  I have had Suse on it and DSL, no usb.  Only Fedora.  Thanks again for your reply

---

### Post by Simian Man on 2009-12-04
> **linuxnovo said:**
> Question:  What does Fedora 11 have that Ubuntu 6.06 does not?  Anyone got any ideas????

A much newer kernel for starters.  I assume you're using such an old version because your hardware is so old.  I'd recommend instead using a more modern system but a lighter windowing system like Openbox or LXDE instead of Gnome.

---

### Post by linuxnovo on 2009-12-05
The Plot thickens 

--------------------------------------------------------------------------------
Still no usb on the acer running ubuntu 6.06, Dapper.

Let me review what is known:

1. Bios is usb enabled.

2. Fedora 11 running as live disk auto mounts the single usb.
Not a hardware problem, an OS problem

3. New Development: I have another laptop a Sony with the same 256 Ram and a faster celeron processor running at 700 MHz about twice as fast as the Acer. The two usbs are both automounting the flashdrive on the Sony.

Everything seems the same fstab and mtab between the Acer and the Sony. The difference is with lsusb and /proc/bus/usb/devices. The Sony has the latter completely populated and the Acer returns nothing. These areas are dynamically populated. How do I populate this on the Acer?

---

### Post by linuxnovo on 2009-12-28
I have two laptops an acer and a sony.  Both are running 6.06, one has the usb ports working, the sony and one not working the acer.  The acer is an older computer than the sony.  A dmesg for the acer will show that the acpi is disenabled because of the age of the BIOs which is 1999 and the cutoff is 2000.  This can be re-enable by modifaction of /boot/grub/menu.lst with the kernel line having the following added to it:

acpi=force, which enables the acpi

iqrpoll, which polls the usb.  This polling will slow the system down a bit, but makes the usb work.

Hope that this will help someone out, because it took me sometime to find this out.

---

### Post by linuxnovo on 2009-12-30
This is a reply to all forums where this question has been submitted.  The above is a more detailed version.  This is just for general update and reference:

Answer:

Thanks for all of your comments and interest in this topic.  I would like to provide some closure on this.  I am afraid that this old acer laptop runs best on ubuntu 6.06 since it was designed about the same time that this computer was built.  I have tried to install other OSs and this one runs best.

I am also running ubuntu 6.06 on a Sony with about the same characteristics with a positive usb detection.  A careful examination of the parallel dmesg printouts reveal that the problem is a difference in the date of the OS.  The acer has a 1999 OS.  The cutoff is 2000, so the vital ACPI is disenabled.  This whole problem can be completely solved by re-enabling the ACPI.  This is down by editing the file: /boot/grub/menu.lst.  The kernel line should have the addition:  acpi=force and iqrpoll.  This has the effect of enabling the acpi and polling for the usb.

Thanks for your help and hope this will help someone sometime.  Happy New Year!

---

