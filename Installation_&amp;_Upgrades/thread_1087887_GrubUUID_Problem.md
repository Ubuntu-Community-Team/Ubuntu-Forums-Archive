---
title: "Grub/UUID Problem?"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by gummyx on 2009-03-05
*********************
*       FIXED       *
*********************

I'll try to make this as clear as possible...

_Setup_:
I recently installed Ubuntu 8.10 onto my laptop. There is one hard drive on that laptop, split into two partitions. My first partition runs Windows XP Home. I've installed Ubuntu 8.10 onto my second partition via Wubi. 

_Situation_:
I played around a bit, everything was fine... until I started messing around with VMWare. Somehow, I managed to get myself an error message each time I tried to boot into Ubuntu, something along the lines of "Error: grldr missing in all devices (CTRL + ALT + DEL to restart)". I tried downloading and using grub4dos, to no avail. I finally gave up, copied the entire Ubuntu folder from my second partition into my first partition, and reformatted my second partition. 

I reinstalled Ubuntu, again, using Wubi, and then replaced the NEW Ubuntu folder with the old one, root.disk, swap.disk, and all (I had gotten really comfortable with all the settings that I had set, and did not want to lose them). However, each time I try to load Ubuntu now, I get an error saying the root UUID was not found, and then get dropped into the BusyBox command line. I have managed to bypass this by going into /dev/disk/by-uuid/ and copying one of the UUID's there and renaming it to the UUID it was looking for (or, pressing "e" at the grub menu and editing root=UUID=... under "kernel"). Hurray, I got everything back! However, this is quite annoying.

So, I googled it, looked all around for possible fixes. I have changed the UUID's in /boot/grub/menu.lst to the correct value as described by blkid, and have taken a look at /etc/fstab, and had no idea what to do with it. Supposedly, editing menu.lst should have fixed that, from what I've read. However, whenever I reboot, I encounter the same error. The incorrect UUID is STILL THERE. I went back to check if my menu.lst was reverted, but it still contained my edited UUID's.

I am now stumped and have absolutely no clue what to do. There seems to be no major error, as far as I can see, but it is just VERY annoying to type in the correct UUID during EVERY SINGLE reboot in order to get Ubuntu running.

Is there some truly permanent fix to this? Am I doing something wrong?
Is there some script I can implement to avoid typing in the correct UUID in every time?

Thanks in advance!

---

### Post by martrn on 2009-03-05
Wubi:
-----
Install(-ing) Ubuntu 8.04/8.10/etc to a workstation or laptop is not the best way of installing Ubuntu but should work fine.  If you have reinstalled the Ubuntu Operating system at any time then re-formatting or re-partitioning a hard drive on a workstation or laptop, could mess up you hard drives UUID's via Wubi or any install method.

Replacing folders ?
-------------------
Reinstalled Ubuntu, again, using Wubi, or any other (better) method is fine but and then replace(-ing) directories in Ubuntu (or any Linux/Unix-like Operating system) by swapping changing folders with the old one, regardless of the directory is not good as all of the settings in in Ubuntu (or any Linux/Unix-like Operating system) are stored in files, there is no very large database bogging down the system kernel.

Basically you (possibly) trashed you settings by copying the directory or as you say folder across.

Now ?????
---------

I would suggest re-installing Ubuntu using an alternative method such as the install CD, as you may have trashed more settings.

If you are sure it is just the UUID settings you changed ??? who knows ??? Then some tips for correcting UUIDs is [-->--HERE--->]("http://ubuntuforums.org/showthread.php?t=947777")

You at the least need to change your file located at '/boot/grub/menu.lst' in order to make sure you UUID's are reflecting the correct ones obtainable from from output of 'sudo blkid'.

---

### Post by gummyx on 2009-03-06
Thank you for your response!

I understand that copying files over and replacing the clean install files was not a very good idea, but I had wanted to keep my settings. And it worked! All my settings were saved. I've already tried all the steps in the link provided, and changed menu.lst as well. 

Allow me to clarify a bit:
All of my changes to /boot/grub/menu.lst STAY after a reboot. However, when booting into Ubuntu, grub does not detect any of my changes, and continues to have all my kernel entries booting from the incorrect UUID. Which means I have to edit the entry manually each time, either with the correct UUID (a pain), or with "root=/dev/sda2" (my Ubuntu partition). It would seem as if my /boot/grub/menu.lst has no effect whatsoever on the entries grub uses to boot Ubuntu.

---

### Post by martrn on 2009-03-06
Did you type in a terminal

```
sudo update-grub
```

to update your grub configuration ?

Why are you booting into Grub using webui ?

Webui ([http://wubi-installer.org]("http://wubi-installer.org/")/) is supposed to boot using the windows boot manager.  Booting on a windows file system (NTFS) should not need any UUID's.

Typing 
```
ls -l /dev/disk/by-uuid
```

gives me :

lrwxrwxrwx 1 root root .......... -> ../../hda1
lrwxrwxrwx 1 root root .......... -> ../../hdb1
lrwxrwxrwx 1 root root .......... -> ../../hdc1
lrwxrwxrwx 1 root root .......... -> ../../hda2

.... etc..... 

but I do not have any 
    .....   root.disk, swap.disk   .....   files (etc.. etc...)
these are real or real hard disks.

If these are wubi files that you are talking of they are files already on a file system and grub will not boot them as such, you would need to chain load then.  

I don't fully understand how webi [http://wubi-installer.org/]("http://wubi-installer.org/") works with disks sorry.  Its one thing I could not understand, as I just wouldn't install a file as a complete file system.

You must realise you are using grub (a linux bootloader) to load a file stored on a windows operating system.  I hope someone else knows how this works, as I don't sorry.

---

### Post by martrn on 2009-03-06
Ok so you have a laptop with one (1) hard drive.  That one hard drive is spit into two (2) partitions. (Your first post).

And on the first partition you have xp, and you also installed webi_linux to two files on the NTFormatted second partition of your hard drive.  Then you copied the two files (root.disk, swap.disk) to you first partition. ??

You then reinstalled Ubuntu, and copied back across you ubuntu old installation files (which is an webi_ubuntu file system), because you wanted that.  You get put at a terminal or busy box, unless you manually edit the menu every time.

try
```
sudo update-grub
```

to update grub ?

I would have gave up and installed linux to the second partion on a true linux file system.

---

### Post by gummyx on 2009-03-06
Thanks again for your responses!

Yes, I have tried using sudo update-grub, but to no avail. =( Although this replaces my /boot/grub/menu.lst with a new one, the kernel list at reboot is still unchanged, with the old UUID and all.

Inputting this into the terminal:
```
ls -l /dev/disk/by-uuid
```
gives me just about the exact same output that you have, with the exception of the UUIDs, of course, and ../..sda1 and ../..sda2 .
I do not have root.disk or swap.disk listed in this output.

In the root directory of my first partition (Windows XP Home), boot.ini contains the following line at the end:
```
c:\wubildr.mbr="Ubuntu"
```
This allows me to choose between XP and Ubuntu at a boot menu. Selecting Ubuntu then gives me the option to press ESC to enter the list of kernels, which I must then edit with the correct UUID or /dev/sda2 in order to boot into Ubuntu.

My /etc/fstab file contains the following:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk     /        ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Originally, /boot/grub/menu.lst reflected the incorrect UUID:
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=76298B8E70A4453C loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
```
This is the wrong UUID, the one that shows before editing at reboot. 

I have tried changing this entry to both 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=E8BC0ECEBC0E976A     /        ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
(the correct UUID)

and 
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
```
(which also works when editing the kernel boot entry manually).

---

### Post by gummyx on 2009-03-06
Nevermind, I found the problem.
C:\wubildr.mbr automatically searches for a "menu.lst". I came across this:
[http://ubuntuforums.org/archive/index.php/t-535231.html](http://ubuntuforums.org/archive/index.php/t-535231.html)
and it described the problem. I still had my Ubuntu folder backups, in the same partition, and wubildr automatically loaded and used my old menu.lst. Of course, the incorrect one. I replaced the old menu.lst in my backups with the real one, and solved the problem.

Thank you very much for you time and your help!

---

