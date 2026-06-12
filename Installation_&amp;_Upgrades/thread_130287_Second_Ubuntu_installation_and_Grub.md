---
title: "Second Ubuntu installation and Grub"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-02-15
If i was to install a second copy of Ubuntu on my harddrive, would Grub automatically be changed to detect the new installation. i.e. can i just create the partition, whack in the CD, install it, then Grub is magically adjusted to give me the choice?

I am currently running Ubuntu BB i386 but want to install 64bit Ubuntu in a second partition and i'm a bit worried about it screwing up Grub so i cant get into either installations.

Any advice would be greatly welcomed.

---

### Post by lha on 2006-02-15
[QUOTE=renzokuken]If i was to install a second copy of Ubuntu on my harddrive, would Grub automatically be changed to detect the new installation. i.e. can i just create the partition, whack in the CD, install it, then Grub is magically adjusted to give me the choice?

I am currently running Ubuntu BB i386 but want to install 64bit Ubuntu in a second partition and i'm a bit worried about it screwing up Grub so i cant get into either installations.

Any advice would be greatly welcomed.[/QUOTE]

Install second grub to the root partition of your new Ubuntu. Then add
```
title           My another Ubuntu
root            (hd0,3)
chainloader     +1
```
to menu.lst. (Replace hd0,3 with the partition having second grub.)

---

### Post by renzokuken on 2006-02-15
ok. how would i go about doing that?

>_<    semi-noob here

---

### Post by lha on 2006-02-15
[QUOTE=renzokuken]ok. how would i go about doing that?

>_<    semi-noob here[/QUOTE]
After partitioning, the installer asks if it is okay to install grub into mbr. Say no, and tell it the name of your root partition.

When installer reboots, you end up in old grub menu. Start old Ubuntu and edit menu.lst.
```
cd /boot/grub/menu.lst
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
In the very end of that file, copy&paste those three lines in my previous post and replace (hd0,3) with correct partition. If you installed to hda3, then you should use (hd0,2). Save and reboot. Select 'My another Ubuntu' to finish installation.

---

### Post by renzokuken on 2006-02-15
[QUOTE=lha]After partitioning, the installer asks if it is okay to install grub into mbr. Say no, and tell it the name of your root partition.
[/QUOTE]


so how do i find out the name of my root partition?

will it just be the partiton i selected to install 64 bit on?

---

### Post by lha on 2006-02-15
[QUOTE=renzokuken]so how do i find out the name of my root partition?

will it just be the partiton i selected to install 64 bit on?[/QUOTE]
Yes.

---

