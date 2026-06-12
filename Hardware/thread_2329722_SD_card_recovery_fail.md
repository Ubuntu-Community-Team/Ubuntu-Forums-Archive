---
title: "SD card recovery fail"
date: 2016-07-04
forum: Hardware
---

### Post by steve234 on 2016-07-04
Hi there. 

I'm in [LUBUBTU] 14.04 LTS.

I removed my phone's SDcard from my Linux box by mistake when there was an "operation pending". Now it crashes the phone and is not mounted by my linux box.

It has 2 partitions:
(1) An ext3 30gb partition (label "30 GB Volume") for media - Iswear this showed up as EXT3 earlier, but now this shows up as FAT so maybe it's FAT?? - Fdisk -l is telling me so!
```
$ sudo file -sL /dev/sdb1
/dev/sdb1: x86 boot sector

```

(2) An ext3 1GB partition (label "sd-ext") that is an extension of my phone's internal memory (via the app Link2SD) - all my apps live here so I'd like to avoid reformatting.

fdisk -l tells me the partitions are /dev/sdb1 and /dev/sdb2

I've tried:[INDENT]
(A) Auto-repair 1GB volume with fsuk (unsuccesful):

```
$ sudo fsck -v /dev/sdb2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
sd-ext: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes
fsck.ext3: unable to set superblock flags on sd-ext


sd-ext: ********** WARNING: Filesystem still has errors **********

```

And the same on the 30GB volume it doesn't recognise as EXT3 so I tried resetting the "dirty bit" as FAT:


(B) resetting the superblock from backup on the 1GB partition:

```
$ sudo mke2fs -n /dev/sdb2
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
62592 inodes, 250110 blocks
12505 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=260046848
8 block groups
32768 blocks per group, 32768 fragments per group
7824 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376

$ sudo e2fsck -b 32768 /dev/sdb2
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdb2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

$ sudo e2fsck -b 98304 /dev/sdb2
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdb2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

$ sudo e2fsck -b 163840 /dev/sdb2
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdb2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

$ sudo e2fsck -b 229376 /dev/sdb2
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdb2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


```
[/INDENT]

Now: 

- The 30GB partition mounts on my Linux box but when I copy files it throws an I/O error.

 - The 1GB partition says "an operation is already pending".

If inserted into the phone "media scanning - SDcard" crashes the phone at around 90%.

I've probably not done this methodically enough / missed something? Any ideas?

---

### Post by weatherman2 on 2016-07-04
I'd be surprised that you were using an ext3 partition on a microSD card used on a phone.  Unless you explicitly made it an ext3 partition in the past (for Linux storage?), it almost certainly was FAT or exFat or something like that.

And if it's not an ext3 partition, then running fsck can't help you.

Next?  Try testdisk maybe?

---

### Post by steve234 on 2016-07-04
Thanks weatherman2,

In that case the 30GB partition was probably FAT.

The 1GB partition is ext3 for sure as it's supposed to mirror the Android (linux based) native filesystem.

---

### Post by steve234 on 2016-07-05
I've made images with testdisk but none of its tools have been able to help.


The SD card is clearly goosed - I've   ordered another one. Hopefully the images will be some assistance in recovering the phone.

---

### Post by sudodus on 2016-07-05
Maybe you can recover some files with ***photorec***, the companion of ***testdisk***; both come from [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

It is possible to recover files of many kinds with photorec (not only photos) even if there is no working file system. It reads the file data from the 'drive surface' alias memory cells. So with some luck you may find a backup file or other file with your address book and other valuable data.

After finishing the recovery process (or cloning the raw data to another drive), you can try to re-partition and re-format the card. The hardware and internal software might still work. You can use ***mkusb*** or ***gparted*** in linux or maybe a formatting tool in the phone for that purpose.

---

### Post by steve234 on 2016-07-05
Thanks - I've tried gparted but it gets I/O errors. Ubuntu doesn't have mkusb and it's not in the repo

---

### Post by sudodus on 2016-07-05
You find detailed instructions here:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

### Post by steve234 on 2016-07-05
Thanks for your help - I tried wiping the first MB and whole device with dd / mkusb wipe. It reported as "done" /"np space left on device" but had no effect. The SDcard still appears with an ex3 partition and won't mount.

I think this SDcard needs to go in the bin. I've backed up what I can with testdisk and ordered another card. Using apps like Link2SD is hard on cards.

Cheers for your help anyway!

---

### Post by weatherman2 on 2016-07-05
The write-protect tab isn't on, is it?

---

### Post by steve234 on 2016-07-06
nope

---

### Post by sudodus on 2016-07-06
> **steve234 said:**
> Thanks for your help - I tried wiping the first MB and whole device with dd / mkusb wipe. It reported as "done" /"np space left on device" but had no effect. The SDcard still appears with an ex3 partition and won't mount.

I think this SDcard needs to go in the bin. I've backed up what I can with testdisk and ordered another card. Using apps like Link2SD is hard on cards.

Cheers for your help anyway!

Did you reboot and then try to create a new partition table and file system after wiping the whole device?

If that failed, I agree that the SD card is damaged beyond what we can repair.

-o-

Good luck with the new card :-)

---

### Post by steve234 on 2016-07-06
Very dead I'm afraid - despite the erase, it still shows in file manger with its label "sd-ext" and the mount error remains.

---

