---
title: "Memory stick doesn't work in multicard reader"
date: 2008-10-17
forum: Hardware
---

### Post by saffagirl on 2008-10-17
HI,

Ive got a dell vostro 1310, dual boot vista. 

My memory card reader so far has only read SD cardsin Ubuntu and can read MS PRO cards (for phone) in Vista, but not in Ubuntu? Anyone got any ideas?

---

### Post by sergiom99 on 2008-10-17
yes, there are lots of threads on this topic in the forums.
There's no kernel support for MS cards yet. Its a Sony proprietary format and someone has to code the drivers for linux with reverse engineering. AFAIK, no one has done it yet, or at least its not included in the kernel.

Good luck.

---

### Post by TombKing on 2008-12-22
Okay thats odd that there is no support. I could get my box running debian from a year ago now to automount a sony memory stick.
It mounts if I use an adapter and one of the USB ports but not the card reader.

So at the least a workaround is get a little usb adapter to read the sony card.:confused:

---

### Post by DrDunkMcNally on 2009-11-17
> **TombKing said:**
> Okay thats odd that there is no support. I could get my box running debian from a year ago now to automount a sony memory stick.
It mounts if I use an adapter and one of the USB ports but not the card reader.

So at the least a workaround is get a little usb adapter to read the sony card.:confused:

Speaking of work arounds, do you know if it's possible to mount it in XP running in Virtualbox? If so any ideas how?  The built in usb recognizer doesn't even seem to want to work all the time, so I doubt it.  But figured I'd ask anyway!

---

### Post by SauloAlessandre on 2010-01-16
Hi,

This is working for me. I have a VGN-FZ140N.

Try this:

$ lsmod | grep tifm
tifm_ms                 6400  0 
memstick               10072  2 mspro_block,tifm_ms
tifm_7xx1               5372  0 
tifm_core               7832  2 tifm_ms,tifm_7xx1

If the result is some like that, so it's working. Now just you need to do is mount the memory stick.

Try dmesg to see where is the block device. For me is some like this:
$ dmesg
...
[289131.410044] tifm0 : demand removing card from socket 0:0
[289186.732084] tifm_core: MemoryStick card detected in socket 0:0
[289186.888218] memstick0: switching to 4-bit parallel mode
[289186.889233]  mspblk0: p1

Mounting device read-only:
$ sudo mkdir /mnt/ms
$ sudo mount /dev/mspblk0p1 /mnt/ms

Now you can access the memory stick in read-only mode

Dont forget to umount device.

$ sudo umount /mnt/ms

---

