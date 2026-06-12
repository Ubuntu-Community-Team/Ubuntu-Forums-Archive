---
title: "Slow USB ZIP drive"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by g4c9z on 2006-09-12
Hi,

I have an IOMEGA external USB ZIP drive.  On my old Linux installations (e.g. I was most recently using Gentoo) it worked at a normal speed.  On Ubuntu, writing data to it goes about 6 or 7 times slower.  I'm wondering if anyone can help me find out why.

Both systems have udev and a 2.6 kernel, although ubuntu has newer versions of both (I installed the newest Ubuntu, Dapper Drake).  It's plugged into a USB 2.0 port, but as far as I know it's just a plain USB drive, so I doubt that makes a difference.  My motherboard is an ASUS A7N8X-X, and the USB port is on the motherboard.  The disk is VFAT (standard Windows format), and the vfat kernel module is loaded.  The parameters in fstab for the disk are the same on both systems.  I think it might be a driver or udev problem or bug, but I don't know enough about the drivers to be able to find out myself.

It's really important to me to get this working at a decent speed, because I have an automatic backup system in place that backs a large amount of data to a zip disk each evening when I shut down my computer, so I don't want it taking half an hour to back up my stuff before it shuts down.  In fact, it's so important that I'd consider abandoning Ubuntu if I can't get it working.

---

### Post by John.Michael.Kane on 2006-09-12
Writing to a zip drive is going to take time. your best bet  other then using a usb hdd. is to let it run the backup's while your not using the machine for a while.

---

### Post by g4c9z on 2006-09-12
"Writing to a zip drive is going to take time."

No it shouldn't.  Like I said, Gentoo did it much faster.  I conducted an experiment to be sure.

---

### Post by John.Michael.Kane on 2006-09-12
Yes writing to a zip drive will take time,and your gentoo experiment is flawed. sorry your comparing a distro that's compile what you need to a distro that gives most of what you need out of the gate.

If the access times on the drive are not up to your standards. i'm not sure what to tell you.

---

### Post by g4c9z on 2006-09-12
Really?  Compiling from source makes that much of a difference with zip drive speeds?  Any suggestions as to what specific software I could compile and install from source to make the most difference in speed?

Maybe I'll try booting another CD-based distribution and see if copying data to it in that setting is as slow.  That way we'll know whether there's actually a problem.

---

### Post by g4c9z on 2006-09-12
The problem is not binary distributions.  I booted the Ubuntu CD itself and tried copying my 27+MB backup file to my ZIP disk from there.  It took only a minute or 2, compared to about half an hour from my installation.  It should not be faster from the CD compared to from my hard drive.  So something is definitely configured wrong, or has a bug.

I don't use the Gnome volume manager that it came with (because it doesn't always act the way I want it to), and I instead have an entry for my ZIP drive /etc/fstab.  That is as follows:

/dev/zipdrive4 		/mnt/zip 	vfat,auto	noauto,users,sync 	0 0

I also get udev to recognize it and create symbolic links (so it can be distinguished from other USB storage devices, such as my digital camera) with the following entry in /etc/udev/rules.d/10-local.rules:

BUS="usb", SYSFS{product}="USB Zip 100", KERNEL="sd?", NAME="zipdrive%n", SYMLINK="%k", OPTIONS="all_partitions"

Anyone see a problem with any of that configuration?  It's exactly the same as I had in Gentoo, so I think it should be fine, but I don't know what else might be different.

---

### Post by Merkwurdigliebe on 2006-11-09
Same problem here.  For some reason the internal USB hub is falling back to 12 Mb/s, and that makes all USB disks, of whatever type, run painfully slow.

It only happens on some machines.  I have two ABIT AMD boards, one works great, and the other has been a nightmare.  I had to build a new kernel to even get it to see the USB drives (any of 5), and even when it does agree to mount them, it runs USB 1.1 instead of 2.0.

This is silly.  The machine works fine in XP 64.  It worked fine with 32-bit 6.10, and 6.06, but the 64-bit version won't mount USB drives correctly.  Centos 4.4 x64 works OK, so it is possible to build a working kernel for this box. It's just the Ubuntu distro that can't seem to get it right.  

It only seems to see one USB bus, but there should probably be two:

daver@pc2:~$ lsusb
Bus 001 Device 005: ID 0917:0207 SmartDisk Corp. 
Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 0000:0000  

daver@pc2:~$ lspci
...
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
...

---

### Post by g4c9z on 2006-11-09
I have a 32-bit 6.06 system, so it's not just a 64 bit problem.  My lsusb and lspci output also seems correct.  But the problem is still there for me.  So it must be a more general problem (I'm guessing bug in Ubuntu that only manifests itself with some hardware).

---

