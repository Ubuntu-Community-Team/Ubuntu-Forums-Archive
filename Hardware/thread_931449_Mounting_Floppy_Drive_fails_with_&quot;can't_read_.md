---
title: "Mounting Floppy Drive fails with &quot;can't read superblock&quot;"
date: 2008-09-27
forum: Hardware
---

### Post by kayvee on 2008-09-27
As the title says, I am having trouble mounting floppy drive. Long story short, I installed Ubuntu on this hard disk when it was sitting in a different computer (but a similar one). Floppy drive used to work fine then. After I moved the hdd to a new home, mounting floppy drive returns with an error.
```

user@replicon:~$ mount /media/floppy
mount: /dev/fd0: can't read superblock
user@replicon:~$ lsmod | grep floppy
floppy                 59588  0 
user@replicon:~$ sudo mount -t vfat /dev/fd0 /media/floppy
[sudo] password for user: 
mount: /dev/fd0: can't read superblock

```

Please help me fix this problem. I need the floppy drive very badly.

---

### Post by vanadium on 2008-09-27
I would reinstall the operating system while the disk is in the proper computer in the first place. Only if all other things are all right is troubleshooting worth the effort.

---

### Post by aer0usa on 2011-04-19
I know this is old, but I was having this problem, and the first reply is NOT helpful. Since this came up in a search I did, perhaps it will help someone else.

The solution for my problem was that I had chosen the wrong filesystem for the mount command. So I had tried

sudo mount -t msdos /dev/fd0 /mnt/floppy

and got the "can't read superblock" message. I opened the floppy in a Windoze PC and found that the floppy's filesystem was "FAT". So this worked:

sudo mount -t vfat /dev/fd0 /mnt/floppy

I found an old Mac floppy and I was able to mount it like so:

sudo mount -t hfs /dev/fd0 /mnt/floppy

So I recommend trying different filesystems in the mount command.

---

### Post by oygle on 2011-10-11
I'm having the same problems, have tried a number of commands. All I want to do is copy some files to the floppy, and then read them in windows.

```
$ sudo mount -t msdos /dev/fd0 /media/floppy0

```

mount: /dev/fd0: can't read superblock

fstab has this entry in it ..

> /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any ideas please ?

Oygle

---

### Post by oygle on 2011-10-11
The floppy must have been faulty. I use another and ..

```
udisks --mount /dev/fd0
```

worked okay.

---

### Post by Erik Swaeb on 2011-11-04
I had the same problem. Using the udisks command solved it. Thanks
[IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG]

---

