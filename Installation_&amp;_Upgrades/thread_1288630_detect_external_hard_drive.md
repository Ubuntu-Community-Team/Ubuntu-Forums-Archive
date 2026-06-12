---
title: "detect external hard drive"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by eneth80 on 2009-10-11
Hi,
Ubuntu on my laptop mounts my external drive automatically, ubuntu 9.04 Jaunty on my desktop computer doesn't. How the drive formatted: was formatted under linux, I do not remember how that is called. On this computer I have no additional /dev/sd* files:
```
**ls /dev/s***
/dev/scd0  /dev/sda2       /dev/sequencer2  /dev/snapshot  /dev/stderr
/dev/sda   /dev/sda5       /dev/sg0         /dev/sndstat   /dev/stdin
/dev/sda1  /dev/sequencer  /dev/sg1         /dev/sr0       /dev/stdout


```there are only these additional files/dirs in /dev  when I connect the HD:
usbdev1.3_ep00
usbdev1.3_ep02
usbdev1.3_ep81

But lsusb sees it:
```
**lsusb #HD not connected**
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**lsusb #HD connected**
[B]Bus 001 Device 004: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
[/B]Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Some other info here below. Thanks,
Alex
```
**less /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b3da8148-7537-45b7-bd70-b23c3b31f945 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=01f38d02-58ba-4105-8043-1fb5395dabee none            swap    sw              0       0
# CD
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
**sudo fdisk -l**
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d377b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30145   242139681   83  Linux
/dev/sda2           30146       30515     2972025    5  Extended
/dev/sda5           30146       30515     2971993+  82  Linux swap / Solaris
**tail -F /var/log/messages**
Oct 11 19:32:20 pepina-desktop kernel: [  581.030380] usbcore: registered new interface driver usb-storage
Oct 11 19:32:20 pepina-desktop kernel: [  581.030386] USB Mass Storage support registered.
Oct 11 19:32:31 pepina-desktop kernel: [  592.100050] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Oct 11 19:32:41 pepina-desktop kernel: [  602.344036] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Oct 11 19:32:58 pepina-desktop kernel: [  619.196038] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Oct 11 19:32:58 pepina-desktop kernel: [  619.444029] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Oct 11 19:33:09 pepina-desktop kernel: [  629.696034] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Oct 11 19:33:09 pepina-desktop kernel: [  629.828649] scsi 2:0:0:0: Device offlined - not ready after error recovery
**lspci**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

---

