---
title: "HP Notebook ACPI problem"
date: 2008-05-02
forum: Hardware
---

### Post by BB_DaKraxor on 2008-05-02
Hi,

I have a HP Compaq 6715b laptop. I'm having some really strange errors.

The 64-bit sound driver for my hardware is quite buggy so I decided to use a 32-bit distro. I've had some problems even at the installation: I had to pass "acpi=off" option to the kernel, otherwise I got a very slow SATA disk read (~200kB/s). This remained the same after the installation. To get a reasonable disk read speed, I need to disable ACPI. But I'd really need it because I run my machine from battery from time to time and I need those power-saving options.

Any ideas how to turn on ACPI without losing support for my SATA disk?

(BTW, strangely on 64-bit, both SATA and ACPI worked fine.)

---

### Post by BB_DaKraxor on 2008-05-05
Hey.

---

### Post by BB_DaKraxor on 2008-05-09
I'd really appreciate your help. Seriously.

---

### Post by aldeby on 2008-05-09
That's strange, have you tried updating your laptop BIOS?

You may also try checking if DMA is disabled for the hard drive: 
assuming /dev/sda is your hard disk device

```

$sudo hdparm /dev/sda

/dev/sda:
 multcount = 0 (off)
 IO_support = 1 (32-bit)
 unmaskirq = 0 (off)
** using_dma = 0 (off)**
 keepsettings = 0 (off)
 readonly = 0 (off)
 readahead = 256 (on)
 geometry = 65535/16/63, sectors = 78126048, start = 0

```

to enable it try with
```

sudo hdparm -d1 /dev/sda

```

---

### Post by BB_DaKraxor on 2008-05-27
Hi,

thanks for the reply, and sorry for being slow.

I haven't tried to update my BIOS, I haven't even thought about it, because I don't know how it would help or how it would be performed.

The result of sudo hdparm /dev/sda:
```
/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0

```

Needless to tell, hdparm -d1 fails:
```
$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Further ideas?

---

