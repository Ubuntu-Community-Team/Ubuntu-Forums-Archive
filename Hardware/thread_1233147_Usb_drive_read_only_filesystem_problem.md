---
title: "Usb drive read only filesystem problem"
date: 2009-08-06
forum: Hardware
---

### Post by hseagle2015 on 2009-08-06
Hi everybody,

today I noticed that couple of directories and files on my Patriot Xporter XT Boost 16 GB USB drive got corrupted :(

Obviously, first I tried to delete the corrupted stuff, but I got a read only error. Since I was able to backup all important data, I decided to format the single FAT32 partition that was on the drive. I tried to do that with Partition Editor and mkfs.vfat, but both of them couldn't do anything because the filesystem is read-only :confused:

To be precise, this is what mkfs.vfat reported (usb drive was unmounted, ofcourse):

```
sudo mkfs.vfat /dev/sde1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/sde1
```

I even tried to erase everything with dd, but without success:

```
sudo dd if=/dev/zero of=/dev/sde1
dd: opening `/dev/sde1': Read-only file system
```

fsck.vfat didn't help either:

```
sudo mkfs.vfat /dev/sde1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/sde1
```

I even tried to format it on Windows, but the format option wasn't even available because of the read-only state.


Since a lot of data was corrupted, I thought that there were some bad sectors involved, but a couple of hours long scan with HDD Regenerator (who never let me down) reported no errors.

So, the question is: is there any way to force formatting of the usb drive or completely deleting the partition? :-k

---

### Post by cvmostert on 2010-07-01
I have the same problem but with a E220 usb modem. it is corrupt and i want to format it and try to re-flash it in windows.. windows does not even read it.

cheers

---

