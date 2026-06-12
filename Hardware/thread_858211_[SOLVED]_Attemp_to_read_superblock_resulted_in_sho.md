---
title: "[SOLVED] Attemp to read superblock resulted in short read"
date: 2008-07-13
forum: Hardware
---

### Post by darkjavi on 2008-07-13
Hi all!
I beg to the gods for some help.

I have an eeepc running Hardy with an sd card where my /home used to live.
Yesterday the laptop run out of battery and it shutdown his-self in a bad way, and the next time it boots complain about missing /home partition.


fdisk -l does not see the sdb1 partition (the one that contains /home)

```

Disco /dev/sda: 4001 MB, 4001292288 bytes
255 cabezas, 63 sectores/pista, 486 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7c34f73f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         486     3903763+  83  Linux

```

Running fsck /dev/sdb1 gives the following output:

```

-@Dark3E:/$ sudo fsck /dev/sdb1
[sudo] password for -: 
fsck 1.40.8 (13-Mar-2008)
[36.50543] Buffer I/O error on device sdb1, logical block 8076608
[36.50789] Buffer I/O error on device sdb1, logical block 8076609
[36.51544] Buffer I/O error on device sdb1, logical block 8076608
[36.51577] Buffer I/O error on device sdb1, logical block 8076609
[36.52654] Buffer I/O error on device sdb1, logical block 0
[36.52856] Buffer I/O error on device sdb1, logical block 1
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

```

Trying fsck /dev/sdb1 -b 8193 gives similar output but complains about device or resource busy instead short read.

That card contains about 800 photos taken in a recent travel across europe, so is a realy valuable data for me.
Any idea of how can I recover the data on the card?

Thanks for you time,

Javier

---

### Post by tech0007 on 2008-07-13
Try 'sudo fsck -p -f' switch to do automatic repair. Worst case, you may have to bring it to some 3rd party data recovery.

---

### Post by darkjavi on 2008-07-13
No luck with fsck -p -f :(

this is what I tried so far:

fdisk - didn't see the partition
gparted - same that fdisk
fsck - complains about short reading or device busy when -b 8193
RIP live cd - kernel panic.

This is weird, I wonder why the partition tools din't see the drive,maybe the card is dead?

Anyway.. Thanks Tech007!

---

### Post by tech0007 on 2008-07-13
Every mounted filesystem has to be synced and unmounted prior to shutdown. That didnt happen to your SD card. :(

---

### Post by darkjavi on 2008-07-16
Solved by itself in the most weird way...
plugged the card on another computer and it worked, after that works again on my little asus... maybe goblins made some fun of me xD

---

