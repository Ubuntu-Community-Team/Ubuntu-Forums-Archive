---
title: "hdparm"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by delbene on 2007-04-24
I was used to configure the hd on my laptop with the command:

```
sudo hdparm -X69 -d1 -u1 -c3 -m16 -k1 /dev/hda
```

but on Feisty it doesn't work, complaining that:

```
/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting keep_settings to 1 (on)
 HDIO_SET_KEEPSETTINGS failed: Inappropriate ioctl for device
 setting xfermode to 69 (UltraDMA mode5)
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
 IO_support   =  0 (default 16-bit)

```

I suspect that this is somehow related to the change feisty made from *hda* to *sda*. Any idea about how to proceed?

---

### Post by delbene on 2007-04-24
Other threads with same problem:

[http://ubuntuforums.org/showthread.php?t=394404](http://ubuntuforums.org/showthread.php?t=394404)
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)
[http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)

---

### Post by nsilva on 2007-04-28
Is it possible that you dont have DMA enabled in your kernel,

Device Drivers --->
  ATA/ATAPI/MFM/RLL support --->
    [*] Generic PCI bus-master DMA support
    [*]   Use PCI DMA by default when available

---

