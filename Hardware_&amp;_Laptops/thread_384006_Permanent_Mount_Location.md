---
title: "Permanent Mount Location"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Blazeix on 2007-03-13
Hi,

 Is there a way to make a certain hard drive always mounts to the same place? I have three usb devices (2 external hard drives and a thumb drive). Right now, my hard drive will mount as usbdisk, usbdisk-1, or usbdisk-2, depending on which items were plugged in first. I have programs that access files on my external hard drive, and I am always having to change the path where they look depending on what the hard drive mounts as. Is there a way to make it so that if my hard drive is attached, it always mounts in the same place? Thanks.

I'm running Ubuntu Edgy.

---

### Post by Dr. Nick on 2007-03-14
Never done this before, but if you didnt know /etc/fstab is what controls mount locations

Look here for some ideas, post 12 looks like it could work
**[http://ubuntuforums.org/showthread.php?p=1659569](http://ubuntuforums.org/showthread.php?p=1659569)**

---

### Post by Blazeix on 2007-03-14
Thanks, that forum post you pointed me to clued me in on several important 'vocab words' which I was then able to Google and figure out how to do it. I figured I would post it here in case other users are looking for how to do it.

This is a useful site that helped me figure out how to do this: [http://reactivated.net/writing_udev_rules.html#builtin](http://reactivated.net/writing_udev_rules.html#builtin)

From the above site:
> udev provides persistent naming for some device types out of the box.

This was exactly what I was looking for. Basically, if you look at the /dev/disk/by-* directories, you will see several symbolic links. For example, if I use ls -Z in /dev/disk/by-id I see this
```

$ ls -Z /dev/disk/by-id
lrwxrwxrwx  root     root                   scsi-1ATA_HTS726060M9AT00_MRH436M4H -> ../../sda
lrwxrwxrwx  root     root                   scsi-1ATA_HTS726060M9AT00_MRH436M4H-part1 -> ../../sda1
lrwxrwxrwx  root     root                   scsi-1ATA_HTS726060M9AT00_MRH436M4H-part2 -> ../../sda2
lrwxrwxrwx  root     root                   scsi-1ATA_HTS726060M9AT00_MRH436M4H-part3 -> ../../sda3
lrwxrwxrwx  root     root                   scsi-1ATA_HTS726060M9AT00_MRH436M4H-part4 -> ../../sda4
lrwxrwxrwx  root     root                   usb-Maxtor_4_A250J0_DEF10A8BC3D5 -> ../../sdc
lrwxrwxrwx  root     root                   usb-Maxtor_4_A250J0_DEF10A8BC3D5-part1 -> ../../sdc1
lrwxrwxrwx  root     root                   usb-SanDisk_U3_Titanium_0000185E79605C7B -> ../../sdb
lrwxrwxrwx  root     root                   usb-SanDisk_U3_Titanium_0000185E79605C7B-part1 -> ../../sdb1

```

I knew that the disk I was interested in was sdc1 (I figured this out using "fdisk -l"). This part of this disk corresponds with "usb-Maxtor_4_A250J0_DEF10A8BC3D5-part1." I put the following entry in my fstab after creating the directory /media/external1:
```

# Always mount this drive to this folder
/dev/disk/by-id/usb-Maxtor_4_A250J0_DEF10A8BC3D5-part1  /media/external1        ext3     defaults,user         0       0

```
As you can see, I'm using the symbolic link usb-Maxtor_4_A250J0_DEF10A8BC3D5-part1 to reference my hard drive, and mounting it in /media/external1. Since the filesystem of my drive is ext3, I specified this as the third argument. I used the options 'defaults,users' to make it so non-root users could mount the disk. If you have a different filesystem, like fat32, you might need to change the options (I'm not sure). I saved fstab, and rebooted. I've rebooted several times with various configurations of usb devices attached, and so far it has worked every time. Thanks!

---

### Post by Dr. Nick on 2007-03-14
yeah, if the partition was fat32 it would be vfat, ntfs for ntfs.

I had played with fstab in the past, but never tried what you did. 

Thanks for making the write up. You may consider posting it to the tips forum.

---

### Post by rare HERO on 2008-02-19
Seems like there is a step missing.  I don't understand what you did:

```
$ always mount this drive to this folder /dev/disk/by-id/scsi-1ATA_HTS541080G9SA00_MPBDP0XKKPLYUM-part2 /media/drive29 fat32 defaults,user 0 0
bash: always: command not found

```


Whats the command?


Figured it out. This post helped me:
[http://ubuntuforums.org/showthread.php?t=432659](http://ubuntuforums.org/showthread.php?t=432659)

---

