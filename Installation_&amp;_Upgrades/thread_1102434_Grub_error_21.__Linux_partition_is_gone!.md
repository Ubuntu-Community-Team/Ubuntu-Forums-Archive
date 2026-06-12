---
title: "Grub error 21.  Linux partition is gone!"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Bakon Jarser on 2009-03-21
Was having problems with the cdrom in Intrepid and it locked up nautilus.  I tried restarting and it froze while shutting down.  I did a hard boot and got grub error 21.  I loaded the live cd to try and restore grub.  Grub couldn't find my boot files.  I tried the GUI way and went through the install to the manual partition editor.  It only shows sda1 (my windows partition) and sda2 (my storage partition).  When I did the install I resized the storage partition to make room for linux.  Now it says that sda2 is back to its original size.  No sign of the linux partition at all.  My dad is computer and he is picking it up today, so my first priority is to get windows to boot.  How do I do this?

---

### Post by meierfra. on 2009-03-21
> so my first priority is to get windows to boot.

Try this in a terminal in the LiveCD:

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

> I tried the GUI way and went through the install to the manual partition editor. It only shows sda1 (my windows partition) and sda2 (my storage partition).

Post the output of

```
sudo fdisk -lu
sudo sfdisk -d 
```

---

### Post by Bakon Jarser on 2009-03-21
Thanks.  I actually just fixed it before I read this.  I used super grub to boot to windows and found a program to restore the mbr.  Linux will just have to wait on that computer for now.

Edit:  No solved button under thread tools anymore?

---

### Post by meierfra. on 2009-03-21
> I used super grub to boot to windows and found a program to restore the mbr.
Great. Super Grub is a handy little tool.

> Edit: No solved button under thread tools anymore? 
Nope. But you can edit the title of your first post, so that it starts with "[Solved]".

> Linux will just have to wait on that computer for now.


If your are lucky,  you just have  problem with the partition table. Then "testdisk" should be able to rescue your ubuntu. Or your file system got corrupted and you have to run a file system check.

---

