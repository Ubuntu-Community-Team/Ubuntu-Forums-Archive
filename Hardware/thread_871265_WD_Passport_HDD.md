---
title: "WD Passport HDD"
date: 2008-07-26
forum: Hardware
---

### Post by mTuran on 2008-07-26
i will buy wd portable hard disk(model name is passport)...have this model any compatible problems with ubuntu ? thanks

---

### Post by madman92 on 2008-07-26
A couple of annoying things. If you plan on using it with windows some of the privileges can get messed up if you rename the device. Also for some reason Flyback doesn't work very well with it. Other than that it works really well.

---

### Post by CharlieFoxtrot on 2008-07-26
I recently purchased a WD Passport drive (160Gb) and installed Ubuntu 8.04 on it so that I can run Linux on my desktop at work without actually installing any software on the computer. Did it following the instructions at:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

Works like a champ! Plug the drive into a usb port on my work machine, boot, and presto, I've got a full-blown Ubuntu machine at work.

---

### Post by mTuran on 2008-07-27
thanks. i want to use for backup my files only.

---

### Post by CharlieFoxtrot on 2008-07-27
Beware that if you plug the drive into a Windows machine, it will try to load some junk software on the machine. Some sort of a file synchronization program and a Google toolbar, if I remember correctly. Turn autorun off to prevent the program on the disk from starting and then delete everything on the drive. If you first plug the drive into a Linux machine, you don't have to worry about it. Just delete everything on the drive. You'll need to decide whether you want to keep the drive's file system at FAT32 or reformat it EXT3 for Linux only. Since I installed Ubuntu on my drive, Ubuntu formatted the drive EXT3 as part of the installation process.

---

### Post by Ozzz on 2008-08-01
I use it on my Toshiba A70 DUAL BOOT laptop. I split it into two drives, one formatted for FAT32 and the other has my Ubuntu on it. I use the FAT32 side for a storage partition for both XP and Ubuntu. I love it!!  

As noted previously, I wiped it clean of installed software and partitioned it right away. Guess since I re-partitioned and formatted it anyway, I could have eliminated the step of deleting the factory installed software.

---

