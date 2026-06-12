---
title: "Please help me make Feisty detect my VAIO's BD/DVD/CD drive"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by Inspector.Gadget on 2007-08-03
I recently got a VAIO AR-series laptop.  The first thing I did was install Ubuntu. So far, I've gotten the Synaptics touchpad, some multimedia keys, 1920x1200 resolution with a recent NVidia driver, and even the Intel 4965AGN wireless card/WPA2 working consistently.  The only problem I've had is getting Ubuntu to detect my DVD drive. It doesn't show up when I cd to /dev and use ls | grep cd or ls | grep DVD, and I'm fairly sure its not there when I run dmesg or lspci.  It works fine in Windows and was able to run (and install from) the 7.04 alternate CD.  I really don't care about Blu-Ray playback or burning yet. I would really like just to be able to read, rip and burn CDs and DVDs.  The install created an entry in fstab that didn't work for me, and /media/cdrom0 is empty.  I've tried to mount the drive manually (though there was nothing to mount) and I'm not sure where to go from here.  Any help would be greatly appreciated!

N.B. Windows tells me that the drive is on ATA channel 0 using an ATAPI interface set to Ultra DMA 2.

Update 1: lspci -vv didn't display any information corresponding to the drive.  Could this be some sort of problem with the master/slave setup? My two hard drives are behind a RAID controller (though not RAIDed) so presumably they're both on the other ATA channel.

Update 2/Solution: Realizing that the drive was attached to an IDE controller, i ran "sudo modprobe ide-cd" and "sudo modprobe ide-generic". The cd one may not be necessary, ide-generic definitely is (the drive didn't spin until it was loaded.)  Thanks, self. :guitar:

---

### Post by lemurian on 2007-08-05
I had the same problem on an IFL90 and found the same solution.  I'm trying to figure out where the root problem is.

---

