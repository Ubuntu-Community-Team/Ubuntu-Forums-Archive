---
title: "Leica Disto 810"
date: 2015-02-13
forum: Hardware
---

### Post by tobias.klaus on 2015-02-13
Hi,

I am trying to get my new Leica Disto 810 recognised and ready to be used under 14.4. I am getting the sound tellung me "new device connected". Hardinfo/sysinfo show me under storage the Disto as scsi5. Yet gparted doesn't know about this, and it also doesn't appear in the filemanager. Leica told me that it should be recognised as a keyboard, yet I don't see anything in relation to that. Most importantly I would like to read out the data from the storage. Ideally, I would be looking for some plugin similar to the windows bluetooth one ([http://www.leica-geosystems.com/en/Leica-DISTO-D810-touch_104560.htm](http://www.leica-geosystems.com/en/Leica-DISTO-D810-touch_104560.htm)) ...

Grüße und Danke 

Tobias

---

### Post by tobias.klaus on 2015-03-08
sudo fdisk -l gives me

Disk /dev/sdc: 62 MB, 62914560 bytes
2 heads, 60 sectors/track, 1024 cylinders, total 122880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdc2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdc3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdc4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order


any ideas?

Thanks

Tobias

---

### Post by tobias.klaus on 2015-03-09
any idea how to get the device recognized and mounted as storage?

Thanks Tobias

---

