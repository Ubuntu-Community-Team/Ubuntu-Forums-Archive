---
title: "cannot detect usb drive"
date: 2016-11-16
forum: Hardware
---

### Post by aab001 on 2016-11-16
[COLOR=#8b4513]Hi  [/COLOR]
[COLOR=#8b4513]I cannot detect the USB flash drive when I plug it!!! I pluged it on windows but still I cannot detect it!!![/COLOR]
[COLOR=#8b4513]this is the output when I used fdisk -l command[/COLOR]
[COLOR=#8b4513]
[/COLOR]
```


[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ sudo fdisk -l [/COLOR]

[COLOR=#8b4513]Disk /dev/sda: 500.1 GB, 500107862016 bytes [/COLOR]
[COLOR=#8b4513]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors [/COLOR]
[COLOR=#8b4513]Units = sectors of 1 * 512 = 512 bytes [/COLOR]
[COLOR=#8b4513]Sector size (logical/physical): 512 bytes / 4096 bytes [/COLOR]
[COLOR=#8b4513]I/O size (minimum/optimal): 4096 bytes / 4096 bytes [/COLOR]
[COLOR=#8b4513]Disk identifier: 0xa82447e9 [/COLOR]

[COLOR=#8b4513]   Device Boot      Start         End      Blocks   Id  System [/COLOR]
[COLOR=#8b4513]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT [/COLOR]
[COLOR=#8b4513]/dev/sda2          206848   195519347    97656250    7  HPFS/NTFS/exFAT [/COLOR]
[COLOR=#8b4513]/dev/sda3       195520512   390832127    97655808   83  Linux [/COLOR]
[COLOR=#8b4513]/dev/sda4       390834174   976771071   292968449    5  Extended [/COLOR]
[COLOR=#8b4513]Partition 4 does not start on physical sector boundary. [/COLOR]
[COLOR=#8b4513]/dev/sda5       390834176   406456319     7811072   82  Linux swap / Solaris [/COLOR]
[COLOR=#8b4513]/dev/sda6       406458368   601767935    97654784   83  Linux [/COLOR]
[COLOR=#8b4513]/dev/sda7       601769984   976771071   187500544   83  Linux [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$  [/COLOR]

```
[COLOR=#8b4513]
[/COLOR]
[COLOR=#8b4513]
[/COLOR]
[COLOR=#8b4513]and this when I used dmesg | tail 
[/COLOR]
```


[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ dmesg | tail [/COLOR]
[COLOR=#8b4513][ 8034.092680] sd 8:0:0:0: [sdb] 30670848 512-byte logical blocks: (15.7 GB/14.6 GiB) [/COLOR]
[COLOR=#8b4513][ 8034.093716] sd 8:0:0:0: [sdb] Write Protect is off [/COLOR]
[COLOR=#8b4513][ 8034.093720] sd 8:0:0:0: [sdb] Mode Sense: 43 00 00 00 [/COLOR]
[COLOR=#8b4513][ 8034.097281] sd 8:0:0:0: [sdb] No Caching mode page found [/COLOR]
[COLOR=#8b4513][ 8034.097286] sd 8:0:0:0: [sdb] Assuming drive cache: write through [/COLOR]
[COLOR=#8b4513][ 8034.101816]  sdb: sdb1 [/COLOR]
[COLOR=#8b4513][ 8034.105945] sd 8:0:0:0: [sdb] Attached SCSI removable disk [/COLOR]
[COLOR=#8b4513][ 8034.341523] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck. [/COLOR]
[COLOR=#8b4513][ 8034.412559] systemd-hostnamed[3622]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname! [/COLOR]
[COLOR=#8b4513][ 8066.221929] usb 2-1.8: USB disconnect, device number 5 [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ sudo  mkdir /media/usb [/COLOR]
[COLOR=#8b4513][sudo] password for aab:  [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ sudo mount /dev/sdb1 /media/usb [/COLOR]
[COLOR=#8b4513]mount: special device /dev/sdb1 does not exist [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ sudo mount /dev/sdb /media/usb [/COLOR]
[COLOR=#8b4513]mount: special device /dev/sdb does not exist [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$ sudo umount /media/usb [/COLOR]

[COLOR=#8b4513]umount: /media/usb: not mounted [/COLOR]
[COLOR=#8b4513]aab@aab-HP-Compaq-8200-Elite-SFF-PC:~$  [/COLOR]

```
[COLOR=#8b4513]
[/COLOR]
[COLOR=#8b4513]what can I do to solve this problem??
[/COLOR]
[COLOR=#8b4513]
[/COLOR]

---

### Post by yancek on 2016-11-16
Check the BIOS to see if it is detected there.  If not, it won't be detected on your operating system.

---

