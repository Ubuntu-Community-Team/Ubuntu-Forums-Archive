---
title: "usb external drive will not mount"
date: 2010-07-27
forum: Hardware
---

### Post by rflores2323 on 2010-07-27
my external drive will not mount anymore for some reason. it was working a couple of days ago.  It turns on and everything however will not mount. 

below are some outputs.   the drive is a seagate 500 gb external usb drive. 

```
xbmc@xbmc-desktop:~$ lsusb
Bus 002 Device 003: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xbmc@xbmc-desktop:~$ sudo fdisk -l
[sudo] password for xbmc: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa2bebe2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38350   308046343+  83  Linux
/dev/sda2           38351       38913     4522297+   5  Extended
/dev/sda5           38351       38913     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f878

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465135104    7  HPFS/NTFS
xbmc@xbmc-desktop:~$ dmesg | tail
[   32.945401]   domain 1: span 0-3 level MC
[   32.945409]    groups: 0,2 (__cpu_power = 2048) 1,3 (__cpu_power = 2048)
[   32.945430] CPU3 attaching sched-domain:
[   32.945438]  domain 0: span 1,3 level SIBLING
[   32.945447]   groups: 3 1
[   32.945460]   domain 1: span 0-3 level MC
[   32.945468]    groups: 1,3 (__cpu_power = 2048) 0,2 (__cpu_power = 2048)
[   35.884543] eth0: no IPv6 routers present
[  962.672036] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  962.820271] hub 1-0:1.0: unable to enumerate USB device on port 3
xbmc@xbmc-desktop:~$ 

```

---

### Post by rflores2323 on 2010-07-28
any help?

---

