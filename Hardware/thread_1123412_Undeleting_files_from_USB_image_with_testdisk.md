---
title: "Undeleting files from USB image with testdisk"
date: 2009-04-12
forum: Hardware
---

### Post by DrSpirograph on 2009-04-12
Hi,
I'm trying to recover some files from a USB drive with testdisk, but it seems to think the image I have is corrupted. Can anyone offer me some advice?

The USB drive is actually an Olympus MS100 voice recorder, but it works just like a USB drive when plugged in.

For safeties sake, rather than work directly on it, I took an image of it and the partition:
```
dd if=/dev/sdc of=disk-image.dd
dd if=/dev/sdc1 of=partition-image.dd
```

The image mounts just fine
```
sudo mount -o loop partition-image.dd /mnt
```
mounts it using vfat, and I can access it just fine.

But using testdisk (v6.10, downloaded from the website and installed via alien)
```
testdisk disk-image.dd
```
And I go to analyse it, I get
```
Invalid FAT boot sector
 1 * FAT16 >32M               0   1 45     7 246 47     127893
 1 * FAT16 >32M               0   1 45     7 246 47     127893

```
and after I do a quick search, and a deeper search, it can find no partitions.

**Note:** The disk is not corrupted, i just want to recover some files that were accidentally deleted, so I'm not sure why I'm getting this.

If I go to Advanced, and choose Undelete, it says
```
 1 * FAT16 >32M               0   1 45     7 246 47     127893
Directory /

No file found, filesystem seems damaged.
```

I've tried it against the full disk image and the partition image, I've tried using Intel, or None for the partition table type, all to no avail.

Does anyone know how I can get it to recognise the partiton?

---

