---
title: "Can't mount audio recording device ZOOM H4 via USB"
date: 2011-10-26
forum: Hardware
---

### Post by aldi65 on 2011-10-26
I'm using Ubuntu version 11.10

I want to copy Files ('*.mpg') from a ZOOM H4 audio recording device to my computer.

I connect the ZOOM H4via USB to the Computer. The H4 display shows the text "Now connecting to PC". But I don't get it mounted.

I've already read two some other threads concerning similar problems, which didn't help for me ([http://www.oreillynet.com/cs/user/view/cs_msg/89091](http://www.oreillynet.com/cs/user/view/cs_msg/89091), [http://ubuntuforums.org/showthread.php?t=1080518](http://ubuntuforums.org/showthread.php?t=1080518)) 

In Detail:
```

$ dmesg | tail -n 6
[13545.432065] usb 3-2: USB disconnect, device number 5
[13599.452035] usb 3-2: new full speed USB device number 6 using uhci_hcd
[13599.624232] scsi7 : usb-storage 3-2:1.0
[13600.629076] scsi 7:0:0:0: Direct-Access     ZOOM     H4 SD R&W        0.01 PQ: 0 ANSI: 2
[13600.662472] sd 7:0:0:0: Attached scsi generic sg4 type 0
[13600.674083] sd 7:0:0:0: [sdc] Attached SCSI removable disk
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 003: ID 045e:001d Microsoft Corp. Natural Keyboard Pro
Bus 002 Device 004: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 006: ID 1686:0040 ZOOM Corporation 

```lshw shows the device:
```
sudo lshw -C disk
...
  *-disk
       description: SCSI Disk
       product: H4 SD R&W
       vendor: ZOOM
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       version: 0.01
       serial: /
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdc

``` Looking for *sdc* below /dev/ I find:
```

$ find /dev -ls | grep sdc
... /dev/sdc
... /dev/disk/by-path/pci-0000:00:1d.1-usb-0:2:1.0-scsi-0:0:0:0 -> ../../sdc
... /dev/disk/by-id/usb-ZOOM_H4_SD_R_W-0:0 -> ../../sdc
... /dev/block/8:32 -> ../sdc

```I've cutted the first columns in the output for better readability. Except for that, the output is complete. Especially there are no devices /dev/sdc1, 2,... and there is no soft link on something like sdc below /dev/disk/by-label/.

A manual mount has no success (neither with nor without option '-f vfat'):
```

$ sudo mkdir /media/zoom
$ sudo mount /dev/sdc  /media/zoom/
mount: no medium found on /dev/sdc
$ sudo mount -t vfat /dev/sdc  /media/zoom/
mount: no medium found on /dev/sdc


```Nautilus shows the device with the following data (translated in English)

[LIST]
[*]Name: ZOOM H4 SD R&W
[*]Type: unknown type (application/octet-stream)
[*]Size: unkonwn
[*]Ort (in English: Place? Location?): computer:///
[*]Datenträger (in English: Medium?): unknown
[*]Accessed: unknown
[*]Changed: unknown
[/LIST]
Has someone any hints what I could try or look for? Shouldn't there be devices like /dev/sdc1 as well? It seems to me that the computer does not recognise the file system on the H4. Are there other mount options I should try?

---

### Post by xuxaxuxa on 2011-10-30
Hrm... I think the problem is that you should be getting "sdc1" or similar in dmesg, rather than just "sdc".  Do you see any references in the output of dmesg to something like that?  For example, after connecting my Zoom and selecting "connect to PC", the following shows up in my dmesg (I'm using Fedora 14 at the moment) :

[root@lugtop xuxa]# dmesg | tail -n 6
[ 2454.968424] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 2457.558748] sd 7:0:0:0: [sdc] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 2457.561747] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 2457.571741] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 2457.571749]  sdc: sdc1
[ 2458.842476] SELinux: initialized (dev sdc1, type vfat), uses genfs_contexts

If you find a reference to a specific partition (sdc1, sdc2, etc), then you'll use

sudo mount -t vfat /dev/sdc1 /media/zoomsudo mount -t vfat /dev/sdc  /media/zoom/

Does that help?

---

### Post by aldi65 on 2011-11-01
Thanks to xuxaxuxa for the response. 

> I think the problem is that you should be getting "sdc1" or similar 
> in dmesg, rather than just "sdc".

Propably your right. I should be getting something like that, but the dmesg output stops after the line "Attached SCSI removable disk".

Meanwhile I tried to connect it with a Windows XP Computer which failed, too. So I might have a Hardware issue on the H4 side. I'll now try to read the memory card with a usb card reader...

Ooops. There is no memory card in the H4. Putting one in and everything works (just auto-mounting - everything's fine!).

So as usual, the main issue sits about 30 cm in front of the monitor...

Thanks anyway for your help!

---

