---
title: "Want to do a clean install"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by royrules22 on 2009-02-26
I have a 7.xx installation on my laptop (circa 2006) that I just want to nuke and install the latest 8 flavor on. I want nothing left over from that previous version (I've already copied over the needed files to my Windows partition). 

The only problem is that I want this to not screw up my Windows partition. Can I just ask the installer to install over my old ext3+swap partition that contains the 7.xx? 

Also I assume this clean install will replace my old GRUB loader? I've edited GRUB to list Windows XP as the first choice and limit the number of kernel installations it shows to 3. I totally forgot how I did so I'd appreciate any help in reminding me how to edit the GRUB loader again...

Thanks

---

### Post by oldos2er on 2009-02-26
You could print out a copy of your /boot/grub/menu.lst so that if you need it, it's right there in front of you. But installing a newer version of Ubuntu should update Grub properly so that you needn't do any editing.

 Backup anything on Windows that's important to you, then boot the LiveCD and use manual installation. Point the installer to your current Ubuntu partition.

---

### Post by 73ckn797 on 2009-02-26
Following the advice of "oldos2er" should work fine.

I would format the partition "ext2" so that you can access Ubuntu from Windows.
Look for "Ext2IFS_1_11.exe" on the web and install that in Windows to be able to read the "ext2" file system. Then you can move files between the two systems.

---

### Post by royrules22 on 2009-02-26
I already have a program to be able to access ext3 files from Windows

---

### Post by 73ckn797 on 2009-02-27
> **royrules22 said:**
> I already have a program to be able to access ext3 files from Windows


ext3? what is that file I need to look for? I will use that myself.

---

### Post by royrules22 on 2009-02-27
I use [IFS drives]("http://www.fs-driver.org/index.html"). I know it says for Ext2 files but it works for my Ext3 partition

---

### Post by 73ckn797 on 2009-03-01
> **royrules22 said:**
> I use [IFS drives]("http://www.fs-driver.org/index.html"). I know it says for Ext2 files but it works for my Ext3 partition

I use that one but it does not read ext3. I have reloaded it several times.

---

### Post by royrules22 on 2009-03-01
Weird because it does for me. 

Anyway I just had a successful re-install

---

