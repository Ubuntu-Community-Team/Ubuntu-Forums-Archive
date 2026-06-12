---
title: "Dual Booting isn't working"
date: 2008-08-26
forum: General Help
---

### Post by tman007 on 2008-08-26
Hello all. Forgive me, i know this question has been asked before, but I can't find an answer in the forums that directly applies to my problem. I recently built my own PC with an AMD Phenom 9550 processor. I installed XP Pro 64. I have also installed a 2nd hard drive and installed 8.04 on that drive, with intent to set up a dual boot system. I am new to linux in general, let alone Ubuntu, so I am not as proficient as most. Still getting my legs under me, so to speak. The problem I have is when I installed Ubuntu and rebooted, it went directly to XP and didn't offer a chance to boot to Ubuntu. I know it had to be something I did/didn't do that created this problem. When I set my partition, I used the full hard drive so there are no other partions, other than the swap partition. I also chose "primary drive" and had it set as "/". I don't know what else to do. I have googled the problem and all the items that come up are for when the system boots to Ubuntu and doesn't boot to windows, which is reverse of my problem. Thanks in advance for any help, and sorry I am so verbose.

---

### Post by eggdeng on 2008-08-26
```
something I did/didn't do
```
Just guessing but I suspect that what you didn't do was tell the installation program to write the bootloader to the MBR on the first HDD, so it has installed to the second.
In your shoes, I would remove the W*nd*ws disk (you might need to configure the Ubuntu drive as primary master) to see if you can boot into Ubuntu. If you can do that, set up the W*nd*ws drive as slave, reboot and run
```
sudo fdisk -l
```
If all goes well & fdisk sees both OSes, you should be able to sort out the boot problem by editing the /boot/grub/menu.lst. Let us know how you get on.

---

### Post by WRDN on 2008-08-26
If you're using 2 Hard Drives, then you could change the jumpers on the drives. Make the HDD with ubuntu on it the Master drive, while the HDD with Windows should be the slave drive. You may be able to set the primary HDD to boot from in the BIOS also. This way, it will find the bootloader on the second drive before the first, and load GRUB. Alternatively, [reinstall GRUB on the second HDD]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by tman007 on 2008-08-26
Thanks for the help. I'll give it a shot, though i may try to reinstall grub. If all else fails, i will just reinstall and have the disk bootloader configured properly.

---

### Post by sandysandy on 2008-08-26
post output of [COLOR="Blue"]sudo fdisk -lu [/COLOR]from terminal (ubuntu live CD)

see this thread on how to install GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

keep in mind the booting order of HDD and that the BIOS will first see the hdd which is earlier in booting order. 

regards

---

