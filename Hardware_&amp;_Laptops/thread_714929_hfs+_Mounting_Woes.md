---
title: "hfs+ Mounting Woes"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by YinZen on 2008-03-04
Hi, im having some problems with a hfs+ formatted drive i got out of my macbook. Im trying to mount it under ubuntu edgy but its not working. The partition i need to mount is /dev/sda2 and when i run:
```
sudo mount /dev/sda2 /media/sda2 -t hfsplus
```
it returns:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So i ran 'sudo dmesg | tail' and got:
```
sudo dmesg | tail

[17180214.500000] end_request: I/O error, dev fd0, sector 0
[17180226.676000] end_request: I/O error, dev fd0, sector 0
[17180448.140000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[17180448.140000] attempt to access beyond end of device
[17180448.140000] sda2: rw=0, want=2818572296, limit=233769824
[17180448.140000] Buffer I/O error on device sda2, logical block 352321536
[17180448.140000] attempt to access beyond end of device
[17180448.140000] sda2: rw=0, want=2818572296, limit=233769824
[17180448.140000] Buffer I/O error on device sda2, logical block 352321536
[17180448.140000] hfs: failed to load extents file
```

This is pretty much the same message fsck gives on boot, something about buffer I/O errors and logical blocks.
however, when i run fsck in terminal i get: 
```
sudo fsck /dev/sda2 -t hfsplus

fsck 1.39 (29-May-2006)
fsck: fsck.hfsplus: not found
fsck: Error 2 while executing fsck.hfsplus for /dev/sda2

```
or:
```
sudo fsck /dev/sda

fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Also, i thought i'd add that a simple check with parted brings the response:
```
Error: Incorrect magic values in the journal header.
```
It all seems pretty intense to me and i dont understand most of it, it's just i have a hell of a lot of data and work on this partition and it would be pretty bad if its broken. If there isn't any hope can anyone reccomend some recovery programs for ubuntu?
Oh, just thought id mention it's a 120gb sata hdd if that helps and everything looks okay in the partition tables parted outputs.
Thanks alot for reading.

---

### Post by YinZen on 2008-03-04
anyone got any ideas? i know its short notice but i have to send my laptop off to somebody tomorrow with the hdd in so if i dont get my data off it tonight theres no hope :(

---

