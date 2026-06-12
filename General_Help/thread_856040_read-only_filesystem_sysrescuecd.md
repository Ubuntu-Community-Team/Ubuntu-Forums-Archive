---
title: "read-only filesystem sysrescuecd"
date: 2008-07-11
forum: General Help
---

### Post by zeezam on 2008-07-11
I have just created a bootable usb disk (160gb) with sysrescuecd latest version. I have win ready on a ntfs partition and tried with partimage to save the win partition. 

/mnt/cdrom/imagename > save partition.

I got error message, can't create temp file. Either there is not enough with space or can't write to disk - something like that.

I don't know what is wrong. I followed the guide at [http://www.sysresccd.org/Howto_install-usb-stick](http://www.sysresccd.org/Howto_install-usb-stick)

Seems to be read only filesystem. It worked with created image on another disk but after when I try cp copy to my disk with sysrescuecd I got 'read-only filesystem'.

I have created the partition with gparted and formatted it to FAT32

---

### Post by SkonesMickLoud on 2008-07-11
Can you post the output of:

```
cat /etc/fstab
```

---

### Post by zeezam on 2008-07-14
I solved it with making the FAT32 partitions extended. Then I could write to the partition. The problem seemed to be if I boot the with USB disk I can not write to it because it's mounted as cdrom so if I want to write a new image it's maybe best to boot with a sysrescue CD.

---

