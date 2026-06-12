---
title: "Help with GRUB to boot osx on External"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by sendblink23 on 2009-07-19
I just bought another laptop similar to mines(read signature), but without the hard drive, just only the internal usb flash drive.. so yeah I'm making another plan similar to make it work differently....

I want the Grub to boot an External USB Hard Drive that has OSX installed (60gb)

Ubuntu 8.10 is installed on an internal usb flash drive (15gb) of my laptop

This is my: sudo fdisk -l

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+  af  Unknown

Disk /dev/sdb: 16.0 GB, 16064184320 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc77c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1865    14980581   83  Linux
/dev/sdb2            1866        1953      706860    5  Extended
/dev/sdb5            1866        1953      706828+  82  Linux swap / Solaris


What I have configured as in Grub List, that I think is getting close to boot osx is:

> title Leopard
root (hd0,0)
chainloader --force +1

But when I boot with it, it goes: 
Starting Up..
Loading stage2 error

Anyways of fixing this, or making my grub list *boot the external device correctly?

And yes, OSX works perfectly fine on that external hard drive, I've tested it on other computers... my issue is just on this laptop, since it has soldered that internal flash drive, bios only detects that internal flash drive as usb device... (I cannot boot my computer from other usb devices) that is why I want to make this work, to see if I can boot other external OS's using grub.

---

### Post by stmiller on 2009-07-19
You may have to alter the hard drive number:
```

title Leopard
root (hd0,0)
chainloader --force +1 \

```

To perhaps something like

```

root (hd1,0)

```

Each machine has a specific ordering of the particular hard drives connected to it. This varies when plugging in more drives and can be a headache with grub.

---

### Post by sendblink23 on 2009-07-19
Actually I have already used that before it gives: Error 25: Disk Read Error

And the one I use.. which I posted above is the only one that does not give that error, it actually reacts but gives another error.

> title Leopard
root (hd0,0)
chainloader --force +1 


So that is why I say... with the one I used I'm getting close to boot it.

I've already tested other numbers.. and nothing all the same Error 25: Disk Read Error
hd1,0
hd2,0
hd3,0
hd4,0
hd1,1
hd2,1
hd3,1
hd4,1

Its only hd0,0 that gives a different reaction: 
Starting Up..
Loading stage2 error

any other ideas?

---

### Post by sendblink23 on 2009-07-19
I guess i will  re format everything and plan to do 2 partitions to the external hard drive(60gb)... 
1. Ubuntu
2. OSX


Installing OSX first...  then installing Ubuntu

selecting the Grub boot... into the Internal Flash Drive (15gb)


then playing with grub to see... if i can make it work somehow

---

