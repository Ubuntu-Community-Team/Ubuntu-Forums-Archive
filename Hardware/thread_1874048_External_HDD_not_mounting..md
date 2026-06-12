---
title: "External HDD not mounting."
date: 2011-11-02
forum: Hardware
---

### Post by subehsharma on 2011-11-02
My Maxtro portable HDD 320GB is no longer getting mounted or is seen when i connect it to my laptop. It has very important work data and i need to reclaim them asap.

When i connect it to the laptop, MountManager does show it as sdb but nautilus doesn't show it.

I see it here also:


subsharm@subsharm:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04b3:4485 IBM Corp. Serial Converter
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 0d49:7450 Maxtor Basics Portable USB Device

Device Utility also list it. Can somebody tell me what i should do? I have recently erased my windows setup and installed Ubuntu on complete disk.

Thanks in advance.

---

### Post by subehsharma on 2011-11-02
In disk utility when i run SMART Data and in it "Run Self-test" i get the result as "FAILED(Read)"

---

### Post by sanderd17 on 2011-11-02
it shows up as sdb?

Can you try the following:

```

sudo mkdir /media/mydrive
sudo mount /dev/sdb /media/mydrive

```

Do post back any errors you get.

---

### Post by subehsharma on 2011-11-02
subsharm@subsharm:~$ sudo mount /dev/sdb /media/mydrive
mount: you must specify the filesystem type

---

### Post by subehsharma on 2011-11-02
i ran nautilus /mnt and it also didn't show my Maxtor HDD.

---

### Post by subehsharma on 2011-11-02
subsharm@subsharm:~$ sudo fsck /dev/sdb
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by subehsharma on 2011-11-03
Anyone??

---

### Post by sanderd17 on 2011-11-03
Sorry, have got some busy days. Can you try fsck sais?

> **subehsharma said:**
> 

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

so
```

e2fsck -b 8193 /dev/sdb

```

You will probably lose your data on that hdd.

---

