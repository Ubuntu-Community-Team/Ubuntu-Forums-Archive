---
title: "Can't mount an unlocked LUKS encrypted volume"
date: 2008-11-23
forum: General Help
---

### Post by Charlie708 on 2008-11-23
I am having problems trying to mount an encrypted partition.  It is on a USB hard drive that is 500GB.  The entire drive is encrypted with LUKS, under it is an ext3 parition.  The cipher is aes-xts-essiv with a key size of 256 bits, hash is sha256.  Currently loaded modules:

```
# lsmod | grep aes && lsmod | grep dm
aes_i586               15744  0 
aes_generic            35880  1 aes_i586
dm_crypt               21124  0 
crypto_blkcipher       25476  2 xts,dm_crypt
dm_mod                 63432  2 dm_crypt

```

Unlocking it via cryptsetup works perfectly, but here is where the problem arises.  The block device /dev/mapper/seagate exits, but cfdisk sees the actual partition as /dev/mapper/seagate1, and gparted sees it as /dev/mapper/seagatep1.  There is no blockdevice /dev/mapper/seagatep1 either.

```
# mount /dev/mapper/seagate /media/loop
mount: you must specify the filesystem type

```

Running e2fsck tells me that the superblock is bad, and claims that all superblocks in the volume are bad.

What annoys me is that testdisk can correctly see all the files in the volume without making any changes to it, but the system cannot mount it.

My only guess is to what caused the problem is that when I disconnected it last time, I unmounted the volume, but didn't close the crypt.  What can I do to fix this?

---

### Post by Charlie708 on 2008-11-24
I have been looking around, and still can't find anything.  Any help is appreciated.

---

### Post by Charlie708 on 2008-11-27
Anyone?

---

### Post by Charlie708 on 2008-11-30
Nothing?  No one has every had this problem?

---

### Post by Charlie708 on 2008-12-03
Used testdisk 6.10 to get my files out, but it doesn't solve the problem.  Seems to be a DM problem.

---

### Post by bodhi.zazen on 2008-12-03
Did you try:

```
mount /dev/mapper/seagatep1 /media/loop
```

If that does not work, output of 

ls -l /dev/mapper

---

### Post by Charlie708 on 2008-12-06
I did try, but the p1 device did not exist.  The name of the mapper/seagate partition was p1, but there was not p1 device to use.  I have since recovered the data from the partitions with testdisk 6.10, and have reformatted the drives (two 500GB 7200.11 in the same dock, same formatting).

---

### Post by oneLuv on 2009-02-07
Did you solve this problem?  

I am installing Ubuntu on a partition on a dual boot system and I am experiencing this exact problem; where "p1" is added to the name.

Any ideas?

---

### Post by tienhn on 2009-02-18
Wow, I just got into the same problem with one of my USB pen drive. I do not remember what happened but I use to be able to mount the drive OK after entering the password. Now the mount failed. Here is the output of my "cryptsetup status"

/dev/mapper/luks_crypto_1044ef9b-e035-4a2c-83af-1b5168beb581 is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 128 bits
  device:  /dev/mmcblk0p1
  offset:  1032 sectors
  size:    7951080 sectors
  mode:    read/write


I can suck it in and reformat but I would like to learn how to deal with this problem. So anyone have an idea, please help.

Thanks,

---

