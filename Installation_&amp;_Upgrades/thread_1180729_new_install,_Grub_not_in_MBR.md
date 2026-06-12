---
title: "new install, Grub not in MBR"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by New-guy on 2009-06-07
Hi i have just finished installing Ubuntu, i don't know which version im using as i have not had a chance to see it. i used a USB install. everything went OK but i rebooted and i booted straight to XP no Grub at all. i have a live CD of Ubuntu which i am in now. i have tried doing grub-install but i recieve the following:

ubuntu@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully 
ubuntu@ubuntu:~$ su root
Password: 
root@ubuntu:/home/ubuntu# cfdisk 

root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


also tried

root@ubuntu:/home/ubuntu# grub-install /dev/sda1
Could not find device for /boot: Not found or not a block device.

the drive was not mounted when i did this any help would be great.

---

### Post by New-guy on 2009-06-07
OK did this now i am going to reboot

grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

