---
title: "hotplug not creating /dev/hda!"
date: 2005-01-16
forum: Hardware &amp; Laptops
---

### Post by ktulu1115 on 2005-01-16
Ok-

I have an IDE drive in my system but Linux will not recognize it, specifically there is no /dev/hda device file.  Hotplug refuses to detect it.  The rest of my system is SCSI and works perfectly, but I had to temporarily disconnect my IDE storage drive during install - grub installiation was hanging during Ubuntu install; I think it was getting confused which drive to write to.  The drive is detected fine in the BIOS but I see nothing in any logs about the drive itself.  lspci displays my controller, so I know that much is at least working.  I also added ide-disk to /etc/modules and rebooted, hoping hotplug would detect it but to no avail.  My only other thought was to manually create the device node file but then I realized Ubuntu was udev based and this wouidn't be the correct solution, if it even works at all.  Any ideas?

Solved the problem!

Had to manually load ide-generic kernel module.  Once I did a modprobe on it, the ATA drive showed up in /var/log/messages.  After that, I added ide-generic to /etc/modules, and on next reboot it detected and mounted fine (I previously added it to /etc/fstab).

---

