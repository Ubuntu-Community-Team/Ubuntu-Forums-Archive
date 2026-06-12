---
title: "No Menu at start - XP starts immediately"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by Observador Celeste on 2009-09-11
Sorry, I'm kinda new to Ubuntu, so I think this might be a dumb question...
I tried Ubuntu before, and after installing it it would give me a menu where I could choose  which OS to start with. 
I decided to install Ubuntu 8.04.3 (H. Heron) in a HD which originally had only Win XP, but this time it just ignores Ubuntu and it goes straight to XP-
I thought this might be an error during installation, so I decided to insert the CD and reinstall Ubuntu. The disk partition assigned to Ubuntu is not recognized, and with the CD, I only have the option to reassign the HD space that windows XP still has, but I don't have any access to the mew Ubuntu partition..
How can I get the menu to choose between Ubuntu or XP, or at least repair the disk to gain that space back?
Thanks in advance.

---

### Post by XDevHald on 2009-09-11
Here is your solution: [http://ubuntuforums.org/showthread.php?p=7895589](http://ubuntuforums.org/showthread.php?p=7895589)

Let us know if you have any other questions.

---

### Post by drs305 on 2009-09-11
First, welcome to Ubuntu.

It's hard to tell what happened. I suggest you boot to the LiveCD desktop and then you can run a couple of things to see what happened during the attempted install.

Open a terminal (Applications, Accessories, Terminal). Run this command:
```

sudo fdisk -l

```
If you created a Linux partition, you should see something that includes these lines:
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1675    13454406    7  HPFS/NTFS
/dev/sda2            2720        7296    36764752+   f  W95 Ext'd (LBA)
/dev/sda5   *        1676        2719     8385930   83  **Linux**
/dev/sda65           2720        2974     2048256   82  **Linux swap** / Solaris

The two highlighted partitions would be your Linux partition and the swap partition.

If you find something similar, next you can open Gparted to get a graphical idea of what happened during the install:
```
gksudo gparted
```
You can also open it from the Main Menu: System, Administration, Partition Manager.

Take a look and tell us what you have found. At least we will know if Ubuntu was installed and can go from there.

You can also take a look at here if you think you have a good installation:
[How to restore the Ubuntu/XP/Vista bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

