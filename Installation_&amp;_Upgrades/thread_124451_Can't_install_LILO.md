---
title: "Can't install LILO"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Pentagonees on 2006-02-01
Hi,

I am eagerly trying to install Kubuntu 5.10 Breezy Badger. Everything seems to go fine untill I need to install a bootloader... Neither GRUB nor LILO will install. 

I have a Asus A7N8X-E Deluxe Motherboard with the dreaded sil3112 Sata chip... (though not in RAID, just two seperate 80 gig SATA disks, which setup recognizes as SDA and SDB). SDA=win xp and SDB=or should be Kubuntu 5.10). Can anyone point me in the right direction?

---

### Post by taurus on 2006-02-01
Could you at least post your /boot/grub/menu.lst (for GRUB) or /etc/lilo.conf (for Lilo)?  And what kind of error message did you get when you tried to install a bootloader?

---

### Post by Pentagonees on 2006-02-01
I'm afraid that won't work, since I can't get Kubuntu up and running. When trying to install, GRUB immediately halts ("cannot install GRUB to /target/" (where target is /dev/sda)). LILO goes as far as 50% before it crashes ("cannot install LILO to /target/" (again the target here is /dev/sda)). 

I used a win 98 bootdisk and "fdisk /mbr" to be able to use win xp.

---

