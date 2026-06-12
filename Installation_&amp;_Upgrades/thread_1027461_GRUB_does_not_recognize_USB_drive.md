---
title: "GRUB does not recognize USB drive"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by ldupont on 2009-01-01
Hi,

I want to test the new Windows 7 on a USB drive. The latter cannot be installed on a USB drive so I used VMWare to install the OS on my USB drive (/dev/sdb1) as a physical partition. So far so good, I'm able to boot it through VMWare. 

Next I managed to start the booting process up to a certain level by directly booting on the USB drive. It crashes at one point. One reason (among a few) that I assume could cause this is that Windows can only boot from the first partition. So I tried to use GRUB to trick Windows into thinking it is booting from the first partition using the following syntax within menu.lst:

[I]title  Windows
map (hd0,0) (hd1,0) 
map (hd1,0) (hd0,0) 
rootnoverify (hd1,0) 
chainloader +1[/I]

but immediately after selecting Windows at boot time time I get: 

*Error 21: Selected disk does not exist *

Windows doesn't boot at all as it does while directly booting on the USB drive so the problem seems to be that GRUB does not recognize the USB drive at boot time.

However, everything seems fine when I do :
[B]
>>sudo grub-install /dev/sdb[/B]

[I]Searching for GRUB installation directory ... found: /boot/grub 
Installing GRUB to /dev/sdb as (hd1)... 
Installation finished. No error reported. 
This is the contents of the device map /boot/grub/device.map. 
Check if this is correct or not. If any of the lines is incorrect, 
fix it and re-run the script `grub-install'. 

(hd0)	/dev/sda 
(hd1)	/dev/sdb [/I]

Everything also appears to be fine as far as fdisk is concerned : 
[B]
>>fdisk -l [/B]

[I]Disk /dev/sda: 60.0 GB, 60011642880 bytes 
255 heads, 63 sectors/track, 7296 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xcccdcccd 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        6992    56163208+  83  Linux 
/dev/sda2            6993        7296     2441880    5  Extended 
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris 

Disk /dev/sdb: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x7ced2024 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       30402   244196352    7  HPFS/NTFS [/I]

Any idea what I could do next? Thanks.

Louis

---

### Post by ldupont on 2009-01-01
Another precision. Grub not recognising the USB drive at boot time is indeed the issue. Running 
[B]
grub > root (hd1)[/B]

whithin GRUB after Ubuntu is booted doesn't generate any error while I get the [I]Error 21: Selected disk does not exist
[/I] before the system is booted (typing *C* during BootScreen).

---

### Post by unutbu on 2009-01-01
Change:
```
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0) 
```

to
```

map (hd0) (hd1)
map (hd1) (hd0) 
```

---

### Post by ldupont on 2009-01-01
> **unutbu said:**
> Change:
```

map (hd0) (hd1)
map (hd1) (hd0) 
```

Already tried. The problem seems related to the drive recognition by GRUB rather that Windows trying to figure on which drive it is booting on.

```

root (hd1,0) 

```

or

```

rootnoverify (hd1,0)
chainloader +1

```

is what generates the error.

---

### Post by unutbu on 2009-01-01
Have you tried
```

title Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

In other words, put the rootnoverify command before the map commands.

---

### Post by ldupont on 2009-01-01
> **unutbu said:**
> ```

title Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
``` No luck with that either.

---

