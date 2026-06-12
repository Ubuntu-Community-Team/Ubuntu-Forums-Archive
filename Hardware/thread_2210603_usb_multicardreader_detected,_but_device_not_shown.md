---
title: "usb multicardreader detected, but device not shown/available, Ubuntu 12.04"
date: 2014-03-11
forum: Hardware
---

### Post by realjkh on 2014-03-11
[COLOR=#000000][FONT=Arial]I have problems with my usb cardreader in Linux Ubuntu 12.04 . I think the device is detected by the operating system, but not shown in category devices and therefore not available.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have checked the following commands:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cardreader not connected:

[/FONT][/COLOR]
```
USER@USER-VPCEA25EC:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6409 Microdia Webcam

USER@USER-VPCEA25EC:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/USER/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=USER)
/dev/sda2 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/4CA4D15EA4D14B5A type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/327CD6DA7CD69845 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/361ADB7E1ADB3997 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

[COLOR=#000000][FONT=Arial]cardreader with micro-sd card connected:[/FONT][/COLOR]
```
USER@USER-VPCEA25EC:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6409 Microdia Webcam
Bus 002 Device 021: ID 14cd:125c Super Top

USER@USER-VPCEA25EC:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/USER/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=USER)
/dev/sda2 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/4CA4D15EA4D14B5A type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/327CD6DA7CD69845 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/361ADB7E1ADB3997 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

sudo fdisk -l
[sudo] password for USER:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77f5110c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27928575    13963264   27  Hidden NTFS WinRE
/dev/sda2   *    27928576    28133375      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28133376   364473007   168169816    7  HPFS/NTFS/exFAT
/dev/sda4       364478462   625139711   130330625    f  W95 Ext'd (LBA)
/dev/sda5       364478464   433210367    34365952    7  HPFS/NTFS/exFAT
/dev/sda6       501944320   625139711    61597696    7  HPFS/NTFS/exFAT
/dev/sda7       497909760   501934079     2012160   82  Linux swap / Solaris
/dev/sda8       433211392   497901567    32345088   83  Linux

dmesg [just the last lines of the output!]
[11195.873212] usb 2-1.2: Product: Mass Storage Device
[11195.873217] usb 2-1.2: Manufacturer: Generic
[11195.873222] usb 2-1.2: SerialNumber: 125C20100726
[11195.873808] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[11195.874002] scsi11 : usb-storage 2-1.2:1.0
[11196.872337] scsi 11:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[11196.872819] sd 11:0:0:0: Attached scsi generic sg2 type 0
[11196.878942] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[11216.680055] usb 2-1.2: USB disconnect, device number 15
[11248.663928] usb 2-1.2: new full-speed USB device number 16 using ehci-pci
[11248.903959] usb 2-1.2: new high-speed USB device number 17 using ehci-pci
[11248.997457] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[11248.997467] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[11248.997473] usb 2-1.2: Product: Mass Storage Device
[11248.997478] usb 2-1.2: Manufacturer: Generic
[11248.997482] usb 2-1.2: SerialNumber: 125C20100726
[11248.998059] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[11248.998772] scsi12 : usb-storage 2-1.2:1.0
[11249.996821] scsi 12:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[11249.997373] sd 12:0:0:0: Attached scsi generic sg2 type 0
[11250.001521] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[11304.368082] usb 2-1.2: USB disconnect, device number 17
[11349.255534] usb 2-1.2: new full-speed USB device number 18 using ehci-pci
[11349.495569] usb 2-1.2: new high-speed USB device number 19 using ehci-pci
[11349.589079] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[11349.589088] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[11349.589094] usb 2-1.2: Product: Mass Storage Device
[11349.589099] usb 2-1.2: Manufacturer: Generic
[11349.589104] usb 2-1.2: SerialNumber: 125C20100726
[11349.589680] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[11349.589873] scsi13 : usb-storage 2-1.2:1.0
[11350.588456] scsi 13:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[11350.589023] sd 13:0:0:0: Attached scsi generic sg2 type 0
[11350.591868] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[11549.106742] usb 2-1.2: USB disconnect, device number 19
[11661.900041] usb 2-1.2: new full-speed USB device number 20 using ehci-pci
[11662.140080] usb 2-1.2: new high-speed USB device number 21 using ehci-pci
[11662.233579] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[11662.233588] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[11662.233594] usb 2-1.2: Product: Mass Storage Device
[11662.233599] usb 2-1.2: Manufacturer: Generic
[11662.233604] usb 2-1.2: SerialNumber: 125C20100726
[11662.234192] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[11662.234388] scsi14 : usb-storage 2-1.2:1.0
[11663.232944] scsi 14:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[11663.235492] sd 14:0:0:0: Attached scsi generic sg2 type 0
[11663.238969] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[12303.061357] cfg80211: Calling CRDA for country: DE
[12303.999994] wlan0: authenticate with a2:05:43:f3:75:03
[12304.022878] wlan0: send auth to a2:05:43:f3:75:03 (try 1/3)
[12304.259518] wlan0: send auth to a2:05:43:f3:75:03 (try 2/3)
[12304.363523] wlan0: send auth to a2:05:43:f3:75:03 (try 3/3)
[12304.377861] wlan0: authenticated
[12304.379494] wlan0: associate with a2:05:43:f3:75:03 (try 1/3)
[12304.400489] wlan0: RX AssocResp from a2:05:43:f3:75:03 (capab=0x431 status=0 aid=1)
[12304.400569] wlan0: associated
[16693.996812] usb 2-1.2: USB disconnect, device number 21
[16712.351561] usb 2-1.2: new full-speed USB device number 22 using ehci-pci
[16712.591595] usb 2-1.2: new high-speed USB device number 23 using ehci-pci
[16712.685133] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[16712.685143] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[16712.685150] usb 2-1.2: Product: Mass Storage Device
[16712.685155] usb 2-1.2: Manufacturer: Generic
[16712.685159] usb 2-1.2: SerialNumber: 125C20100726
[16712.686294] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[16712.686481] scsi15 : usb-storage 2-1.2:1.0
[16713.684589] scsi 15:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[16713.685137] sd 15:0:0:0: Attached scsi generic sg2 type 0
[16713.691113] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[17520.033230] usb 2-1.2: USB disconnect, device number 23
[17622.276736] usb 2-1.2: new low-speed USB device number 24 using ehci-pci
[17622.372987] usb 2-1.2: New USB device found, idVendor=093a, idProduct=2510
[17622.372997] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[17622.373003] usb 2-1.2: Product: USB OPTICAL MOUSE
[17622.373008] usb 2-1.2: Manufacturer: PIXART
[17622.377104] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input12
[17622.377365] hid-generic 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.2/input0
[18029.260300] usb 2-1.2: USB disconnect, device number 24
[18030.972120] usb 2-1.2: new full-speed USB device number 25 using ehci-pci
[18031.212164] usb 2-1.2: new high-speed USB device number 26 using ehci-pci
[18031.305422] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[18031.305432] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[18031.305438] usb 2-1.2: Product: Mass Storage Device
[18031.305443] usb 2-1.2: Manufacturer: Generic
[18031.305448] usb 2-1.2: SerialNumber: 125C20100726
[18031.306025] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[18031.306206] scsi16 : usb-storage 2-1.2:1.0
[18032.305030] scsi 16:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[18032.305584] sd 16:0:0:0: Attached scsi generic sg2 type 0
[18032.309586] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[18038.267625] usb 2-1.2: USB disconnect, device number 26
[18043.434048] usb 2-1.2: new full-speed USB device number 27 using ehci-pci
[18043.674116] usb 2-1.2: new high-speed USB device number 28 using ehci-pci
[18043.767622] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[18043.767632] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[18043.767638] usb 2-1.2: Product: Mass Storage Device
[18043.767643] usb 2-1.2: Manufacturer: Generic
[18043.767648] usb 2-1.2: SerialNumber: 125C20100726
[18043.768227] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[18043.768422] scsi17 : usb-storage 2-1.2:1.0
[18044.766927] scsi 17:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[18044.767441] sd 17:0:0:0: Attached scsi generic sg2 type 0
[18044.773377] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[18877.756516] usb 2-1.2: USB disconnect, device number 28
[18883.252261] usb 2-1.2: new low-speed USB device number 29 using ehci-pci
[18883.348439] usb 2-1.2: New USB device found, idVendor=093a, idProduct=2510
[18883.348449] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[18883.348455] usb 2-1.2: Product: USB OPTICAL MOUSE
[18883.348459] usb 2-1.2: Manufacturer: PIXART
[18883.352456] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13
[18883.352731] hid-generic 0003:093A:2510.0003: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.2/input0
[32313.790925] usb 2-1.2: USB disconnect, device number 29
[32322.725326] usb 2-1.2: new full-speed USB device number 30 using ehci-pci
[32322.965329] usb 2-1.2: new high-speed USB device number 31 using ehci-pci
[32323.058861] usb 2-1.2: New USB device found, idVendor=14cd, idProduct=125c
[32323.058870] usb 2-1.2: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[32323.058876] usb 2-1.2: Product: Mass Storage Device
[32323.058881] usb 2-1.2: Manufacturer: Generic
[32323.058886] usb 2-1.2: SerialNumber: 125C20100726
[32323.059323] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[32323.059471] scsi18 : usb-storage 2-1.2:1.0
[32324.058168] scsi 18:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[32324.058941] sd 18:0:0:0: Attached scsi generic sg2 type 0
[32324.064521] sd 18:0:0:0: [sdb] Attached SCSI removable disk
```

I already tried the solutions here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/995743](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/995743)

and also I tried 

> [COLOR=#000000][FONT=Arial]On the terminal type "sudo blkid[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial] before inserting the device, this will print all the block devices currently on your system. Now insert the device and type [/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo blkid[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial] again. Now you will see that the new device has been added (either as /dev/sdbx or as /dev/sdcx or as /dev/sddx, where x>=1).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now go to the terminal again and type [/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo mount /dev/sdxx /dir/to/be/mounted/[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial] where xx are the last 2 letters of the device that you just detected.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now, the files will be accessible at the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/dir/to/be/mounted[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. Also make note that you have use [/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial] to copy files into the directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]And before you remove the device, unmount it using [/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo umount /dev/sdxx[/FONT][/COLOR][COLOR=#000000][FONT=Arial]"[/FONT][/COLOR]


Unfortunately after inserting the cardreader and using [COLOR=#000000][FONT=Arial]"[/FONT][/COLOR]sudo blkid[COLOR=#000000][FONT=Arial]"[/FONT][/COLOR] again no new device was shown...
[COLOR=#000000][FONT=Arial]
How can I fix this problem?

greatings, jkh[/FONT][/COLOR]

---

