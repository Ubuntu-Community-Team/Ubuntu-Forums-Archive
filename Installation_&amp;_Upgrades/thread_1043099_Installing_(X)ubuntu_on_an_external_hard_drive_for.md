---
title: "Installing (X)ubuntu on an external hard drive for part-time use"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by purplepaint on 2009-01-18
I'm not very experienced in installing operating systems, so I have no idea how this would work.

I have a desktop running Windows XP which doesn't have enough internal hard disk space to install another operating system for dual-booting.  The "default" operating system for this computer needs to remain as Windows XP (so that anyone switching it on wouldn't have to do anything to boot Windows - someone wanting to boot Xubuntu would just need to press down when presented with the GRUB screen to select it or something).

If I were to install Xubuntu onto a partition on an external hard drive (which is connected to a mains power socket), would it be safe to have the drive switched off/disconnected for the majority of the time and only switched on/connected when someone plans to boot Xubuntu after switching the computer on?  i.e. have Windows boot after however long GRUB is set to start the selected OS without complaining that the disk onto which Xubuntu is installed can't be detected?

---

### Post by Pumalite on 2009-01-18
Should install Grub to the external HH.
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by purplepaint on 2009-01-18
Thanks for the reply.

So, am I right in thinking that I would choose "No" here: [http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location](http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location) and then type (hd1) as the "Device for boot loader installation" during the Alternate Install process?

---

### Post by Pumalite on 2009-01-18
If you have only one internal drive; then most provably the external HH is /dev/sdb1. You have to replace (hd0) in 'Advanced Tab' for /dev/sdb1.
Find out for sure running:
```
sudo fdisk -lu
```

---

