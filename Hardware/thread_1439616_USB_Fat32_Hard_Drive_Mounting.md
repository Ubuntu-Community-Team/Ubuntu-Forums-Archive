---
title: "USB Fat32 Hard Drive Mounting"
date: 2010-03-26
forum: Hardware
---

### Post by chris1379 on 2010-03-26
I am running Ubuntu Hardy 8.04 on a Sony PIII laptop. I have a Simpletech 250GB USB hard drive that I use for backups and a few other things. It is formatted as Fat32 so that I can use it in several platforms. The drive does not automount at boot or when connected to the system. It is automatically mounted by all my other systems, including Win2K on the same laptop. My Ubuntu automatically mounts everything else, including thumb drives and an NTFS USB hard drive. I can manually mount it using

```
sudo mkdir /media/simpletech250
sudo mount -t vfat /dev/sdb1 /media/simpletech250
```

This doesn't work if the NTFS USB hard drive is also connected so that may be a clue. When I enter.

```
sudo fdisk -l
```

I get:
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3986e66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

I would like for the drive to auto-mount or have a script on the desktop that I can just click to mount it but I'm still new at this and it's a little above my head. Can someone help me, please?

Chris

---

### Post by chris1379 on 2010-03-27
OK, it seems this drive just doesn't want to auto-mount. I figured it would be OK to connect it before booting and shut down to disconnect it but that still didn't work. I used the Storage Device Manager to configure it and it added this to my fstab:
```
/dev/sdb1   /media/sdb1     vfat         defaults                            0  0
```I still have to manually mount it and this created a new problem. If the Simpletech 250GB is not connected, I can't use USB thumb drives or my NTFS drive because they will become sdb1. I get the error, "You are not privileged to mount the volume 'STORE'N'GO'" for my thumb drive. Where do I go from here? I did note that the thumb drive is FAT16 and not FAT32 so is there something in the system that tells it not to mount or show a USB connected FAT32 drive? My internal FAT32 partition is normally not mounted but shows in Nautilus. All I have to do is click on it and it mounts. Any ideas here?

Edit: I just found out that it acts the same way from the Ubuntu 8.04 Live CD. I'm going to check it with a partition editor and see what I find. Anything I should look for?

Chris

---

### Post by chris1379 on 2010-03-28
I checked it with several partition editors and everything looks fine. I did notice that one of the flags is LBA, but would that make a difference.

So then I tried some other computers with the 8.04 Live CD. None of them would auto-mount this drive either. However, to my surprise all 3 of them will auto-mount it when running the Ubuntu 9.10 Live CD. This tells me the problem is with Hardy but what is it?

Chris

---

