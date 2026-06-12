---
title: "slow writing speeds external drive Maxtor OneTouch"
date: 2009-02-23
forum: Hardware
---

### Post by hansie99 on 2009-02-23
Hi,

I have a Maxtor OneTouch4 external usb drive and it automounts perfectly in Intrepid Ibex. However, I get very slow writing speeds ( max. 1.5 MB/s) although it's using an usb2.0 port (two actually - one for power the other one power/data). Reading speeds are round 12 MB/s. 

When searching for a solution I came upon lots of people with related problems, but my config is using the USB File System instead of an entry in fstab. 

fdisk -l shows the onetouch4 is recognized as /dev/sdb1 and mountpoint is /media/onetouch4 

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=682b3f82-07da-436f-b6e2-e2b5c4d71814 /               reiserfs notail          0       1
# /dev/sda2
UUID=e1c3f757-c737-40be-9418-cb22257076d2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

When I comment out the last line and restart, it makes no difference, so what's this line all about? 

When I manually mount using MOUNT it still copies at the same speeds. Also the Grub option pci=routeirq doesn't work for me. 

Under windows XP (which I don't use anymore) it worked fine. 

Any ideas how I can speed it up? Any help on clearing this up is highly appreciated. Based on the information I found, most people use an entry in fstab and not the usbfs. Or am I completely wrong here?

Thanks,
Hans

---

