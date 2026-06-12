---
title: "sd card not recognized"
date: 2014-01-01
forum: Hardware
---

### Post by xxlalien on 2014-01-01
Hi,

a 4gb mini SD card ist not recognized with ubuntu 13.04 while Windows can read and write to the card without problems. The model of my computer is VAIO svs15 ... The sd card is not mounted and gparted recognizes it as an "unallocated" 13mb medium. I attached the output of sudo fdisk -lu and of tail -f /var/log/syslog when inserting the sd card.

I would highly appreciate any ideas!!!
thanks for reading
igor igel

> spc@spc-SVS1512Z9EB:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x479608f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT

Disk /dev/mmcblk0: 13 MB, 13107200 bytes
4 heads, 16 sectors/track, 400 cylinders, total 25600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/mmcblk0 doesn't contain a valid partition table

> 
spc@spc-SVS1512Z9EB:~$ tail -f /var/log/syslog
Jan  2 00:57:09 spc-SVS1512Z9EB avahi-daemon[1199]: Registering new address record for 2001:a60:2471:8f01:39a0:4abb:17c8:de6f on wlan0.*.
Jan  2 00:57:09 spc-SVS1512Z9EB avahi-daemon[1199]: Registering new address record for 2001:a60:2471:b01:caf7:33ff:fe25:17ff on wlan0.*.
Jan  2 00:57:09 spc-SVS1512Z9EB avahi-daemon[1199]: Withdrawing address record for 2001:a60:2471:b01:caf7:33ff:fe25:17ff on wlan0.
Jan  2 00:57:18 spc-SVS1512Z9EB avahi-daemon[1199]: Registering new address record for 2001:a60:2471:b01:caf7:33ff:fe25:17ff on wlan0.*.
Jan  2 00:57:18 spc-SVS1512Z9EB avahi-daemon[1199]: Withdrawing address record for 2001:a60:2471:b01:caf7:33ff:fe25:17ff on wlan0.
Jan  2 00:57:33 spc-SVS1512Z9EB kernel: [39275.043674] sdhci: Secure Digital Host Controller Interface driver
Jan  2 00:57:33 spc-SVS1512Z9EB kernel: [39275.043679] sdhci: Copyright(c) Pierre Ossman
Jan  2 00:58:04 spc-SVS1512Z9EB wpa_supplicant[2619]: wlan0: WPA: Group rekeying completed with 9c:c7:a6:5c:df:29 [GTK=TKIP]
Jan  2 01:08:04 spc-SVS1512Z9EB wpa_supplicant[2619]: wlan0: WPA: Group rekeying completed with 9c:c7:a6:5c:df:29 [GTK=TKIP]
Jan  2 01:13:40 spc-SVS1512Z9EB kernel: [40240.390656] mmc0: card 0002 removed
Jan  2 01:13:56 spc-SVS1512Z9EB kernel: [40256.235637] mmc0: SD Status: Invalid Allocation Unit size.
Jan  2 01:13:56 spc-SVS1512Z9EB kernel: [40256.237559] mmc0: new high speed SD card at address 0002
Jan  2 01:13:56 spc-SVS1512Z9EB kernel: [40256.237788] mmcblk0: mmc0:0002 SD016 12.5 MiB 
Jan  2 01:13:56 spc-SVS1512Z9EB kernel: [40256.239159]  mmcblk0: unknown partition table


---

### Post by raphael-platte on 2014-01-01
Try formatting it in windows.

---

### Post by xxlalien on 2014-01-02
Thank you, I tried that but it did not help. I used the standard options suggested by Windows. Should I change anything?

---

### Post by andyfied on 2014-01-02
Have you tried using gparted as fdisk suggested?

---

### Post by xxlalien on 2014-01-02
Yes as far as I remember gparted used to detect it as an unkown 13 mb  drive and could not make any changes on it. Right now however it does not recognize it at all. By the way I tried to format the card with my Android phone and it did not help too.

---

