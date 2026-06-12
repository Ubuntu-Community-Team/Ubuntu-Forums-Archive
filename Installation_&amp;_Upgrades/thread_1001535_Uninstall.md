---
title: "Uninstall?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by Godleflopest on 2008-12-04
Sooo.
I'm brand new to Ubuntu and I got my free disc in the mail the other day. I installed it onto my hard drive and did the mandatory restart, but GRUB had error 21, and I now have no idea how to fix it. Anyone have this problem/know what to do?

---

### Post by inobe on 2008-12-04
hi and welcome


we need some more information !

is this a dual boot setup, if so' is it xp or vista


as for grub 21, it is a hard disk error

---

### Post by Godleflopest on 2008-12-04
Alright.
Uhm. 
I have XP, and I installed it onto a portable hard drive that I never unplug because my built in hard drive was having errors partitioning.
So no, not dual booting.

---

### Post by caljohnsmith on 2008-12-04
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by Godleflopest on 2008-12-04
Alright. 
I got my XP disc and got it back, I'm going to try just a basic install now. 
Thanks for the help though guys. :]

---

### Post by jmacx81 on 2008-12-04
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

I think you scared him

---

### Post by Godleflopest on 2008-12-04
Hahaha. Yeah. Pretty much.

Okay so. 
I did the install again, and all went well, but then I got error 21 again. :/ When I partitioned my hard drive, I didn't divide it up, should I have? I just made one big 20gig partition then said use all available space. 
What did I do wrong?
And remember, I'm brand new to this, so baby steps please. :P

---

### Post by Godleflopest on 2008-12-04
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

Alrighty. Here ya' go.

```
ubuntu@ubuntu:~$ sudo fdisk -lu



Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x353d353c



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

```

```
ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sda

eb48

```

```
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda

0483

```

---

### Post by Godleflopest on 2008-12-05
Okay.
I got it working and running.
Thanks guys soooooo much for trying to help.

---

