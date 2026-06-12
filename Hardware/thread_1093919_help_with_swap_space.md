---
title: "help with swap space"
date: 2009-03-12
forum: Hardware
---

### Post by dvirdc on 2009-03-12
Heya guys
im really new to linux and ubuntu and just finished installing it after i got a virus on windows.
im on a eeepc 1000h, travelling all over the world.
well i followed a nice manual about installing ubuntu and succesfully done everything including wireless. now im stuck  with one thing only.
when i installed ubuntu i had to repartition my /dev. well i backuped everything on d: drive before i left windows and thats where everything went wrong. i "linux-swap"ed /dev/sda2 and that was d: drive with all my files in it.
is there anyway i can still save everything?
please help

---

### Post by cantormath on 2009-03-12
> **dvirdc said:**
> Heya guys
im really new to linux and ubuntu and just finished installing it after i got a virus on windows.
im on a eeepc 1000h, travelling all over the world.
well i followed a nice manual about installing ubuntu and succesfully done everything including wireless. now im stuck  with one thing only.
when i installed ubuntu i had to repartition my /dev. well i backuped everything on d: drive before i left windows and thats where everything went wrong. i "linux-swap"ed /dev/sda2 and that was d: drive with all my files in it.
is there anyway i can still save everything?
please help

What exactly do you mean by "Linux-swap"ed?

How many hardrives do you have?  When you did the installed, did you pick guided (entire disk)?  If you only have one drive and you did that, your entire drive was formated and used for linux.  

open a terminal.  blow it up a bit, and type:
sudo fdisk -l

should tell you what your disk situation looks like.  Post it up to give us an idea.

---

### Post by dvirdc on 2009-03-12
hi mate. 
first- thanks for fast answer :)
that's the situation:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5220    41929618+  83  Linux
/dev/sda2            5221        9724    36178380   82  Linux swap / Solaris
/dev/sda3            9725        9729       40162+  82  Linux swap / Solaris
$ 


when i didnt touch  /dev/sda2, i just changed it from ntfs  to swap.
well.. hopefully i can still save my files :/
what do you say?

---

### Post by taurus on 2009-03-12
You mean you want to recover your files on /dev/sda2?  Hopefully, TestDisk can do something about that.  Make sure you don't have /dev/sda2 mounted though.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by teaker1s on 2009-03-12
or knoppix live cd

---

