---
title: "udev/hotplug not creating IDE dev nodes"
date: 2005-01-17
forum: Installation &amp; Upgrades
---

### Post by ktulu1115 on 2005-01-17
Ok-

I have an IDE drive in my system but Linux will not recognize it, specifically there is no /dev/hda device file. Hotplug refuses to detect it. The rest of my system is SCSI and works perfectly, but I had to temporarily disconnect my IDE storage drive during install - grub installiation was hanging during Ubuntu install; I think it was getting confused which drive to write to. 

-The drive is detected fine in the BIOS but I see nothing in any logs about the drive itself
-lspci displays my controller, so I know that much is at least working
-I also added ide-disk to /etc/modules and rebooted, hoping hotplug would detect it but to no avail
-I've also tried messing around with the /etc/udev/udev.rules file, adding a line for an IDE disk, but again - no luck.

My only other thought was to manually create the device node file but then I realized Ubuntu was udev based and this wouidn't be the correct solution, if it even works at all.  Any ideas?

---

### Post by hardcandy on 2005-01-17
How about making a fstab entry for it? 
/dev/hda1       /          ext3   defaults,errors=remount-ro 0       1

---

