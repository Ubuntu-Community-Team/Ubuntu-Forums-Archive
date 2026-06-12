---
title: "[SOLVED] Hard Drive click/read"
date: 2008-09-30
forum: Hardware
---

### Post by Mr Rough on 2008-09-30
I've searched all over for my specific issue and haven't found anything yet.

Essentially my harddrive sounds like it is reading briefly every second or so, not quite a click but maybe a quick spinup or some such. Reading online I believe it is probably the power management on the drive.

Unfortunately hdparm doesn't appear to work for me so I'm out of ideas.

Here is a quick rundown of what I've done:

Hardware Info:
---
```

kirk@Rosemary:~$ sudo lshw -businfo -C disk
Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/cdrom1  disk        DVDRAM GSA-H42N
                  /dev/cdrom1  disk        
scsi@2:0.0.0      /dev/sda     disk        251GB WDC WD2500YS-01S
scsi@7:0.0.0      /dev/sdb     disk        251GB WDC WD2500YS-01S

```


OS (Ubuntu 8.04)
---
```

kirk@Rosemary:~$ uname -a
Linux Rosemary 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

hdparm
---
```
kirk@Rosemary:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30515/255/63, sectors = 490234752, start = 0

```

```

kirk@Rosemary:~$ sudo hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30515/255/63, sectors = 490234752, start = 0

```

Disable power management
---
```

kirk@Rosemary:~$ sudo hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30515/255/63, sectors = 490234752, start = 0

```

```

kirk@Rosemary:~$ sudo hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error

```

```

kirk@Rosemary:~$ sudo hdparm -B 255 /dev/sdb

/dev/sdb:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error

```

I'm out of ideas. I've been using Windows because this doesn't happen there and I'm concerned for my hardware.

Does anyone have an idea about this or how to fix this issue? Any help is appreciated. Thank you for your time.

---

### Post by Mr Rough on 2008-10-01
Shameful bump :(

---

### Post by Mr Rough on 2008-10-17
Well I figured out the issue, just in case someone else comes across this bizarre issue.

I did a ps -ax and noticed these:

```

 5408 ?        S      0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
 5410 ?        S      0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
 5412 ?        S      0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
 5414 ?        S      0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
 5417 ?        S      0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)

```

My system does a read every two seconds and I figured it out. I unplugged a memory card reader and the sound stopped. In fact my system is way more responsive now.

That hounded me for months. Seems like a bug but at least it is fixed and it isn't hard drive related.

---

