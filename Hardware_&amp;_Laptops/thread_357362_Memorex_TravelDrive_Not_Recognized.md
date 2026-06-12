---
title: "Memorex TravelDrive Not Recognized"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by JLuv on 2007-02-09
I've been searching and searching with no answer. No USB thumb drives will work under Ubuntu 6.10. They don't even blink.

My 256MB Memorex TravelDrive worked when I first installed Ubuntu but after a few restarts between WinXp & Ubuntu, it mysteriously stopped working. I've tried different USB drives but none will work. I've tried different USB ports and none work. I even formatted the drive (fat32) and it won't work. However, my iPod Nano works perfectly.
I have automount turned on, btw.

cat /etc/fstab only shows my harddrive, no sda...
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2e538560-72e3-4cb7-88cd-15e0a70b3651 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=14e07a66-32b6-4d05-943b-544aed2200d1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

sudo fdisk -l shows only my hard drives...
```
$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9306    74710282+   7  HPFS/NTFS
/dev/hda3            9307        9729     3397747+  db  CP/M / CTOS / ...

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4863     1622565    5  Extended
/dev/hdb5            4662        4863     1622533+  82  Linux swap / Solaris
```

dmesg | grep -i usb mentions some drives but I think it may be my iPod...
```
$ dmesg | grep -i usb
[17179577.700000] usbcore: registered new driver usbfs
[17179577.700000] usbcore: registered new driver hub
[17179577.700000] USB Universal Host Controller Interface driver v3.0
[17179577.704000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.704000] usb usb1: configuration #1 chosen from 1 choice
[17179577.704000] hub 1-0:1.0: USB hub found
[17179577.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.812000] usb usb2: configuration #1 chosen from 1 choice
[17179577.812000] hub 2-0:1.0: USB hub found
[17179577.920000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[17179577.920000] usb usb3: configuration #1 chosen from 1 choice
[17179577.920000] hub 3-0:1.0: USB hub found
[17179578.028000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179578.032000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.032000] usb usb4: configuration #1 chosen from 1 choice
[17179578.032000] hub 4-0:1.0: USB hub found
[17179578.052000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.864000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179579.064000] usb 1-1: configuration #1 chosen from 1 choice
[17179579.312000] usb 4-7: new high speed USB device using ehci_hcd and address 4
[17179579.640000] usb 4-7: new high speed USB device using ehci_hcd and address 5
[17179581.152000] usb 4-7: new high speed USB device using ehci_hcd and address 10
[17179583.920000] usb 4-7: new high speed USB device using ehci_hcd and address 20
[17179584.928000] usb 4-7: new high speed USB device using ehci_hcd and address 23
[17179585.688000] usb 4-7: new high speed USB device using ehci_hcd and address 25
[17179587.700000] usb 4-7: new high speed USB device using ehci_hcd and address 32
[17179588.460000] usb 4-7: new high speed USB device using ehci_hcd and address 34
[17179588.752000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
[17179588.752000] usbcore: registered new driver usblp
[17179588.752000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179639.612000] usb 4-8: new high speed USB device using ehci_hcd and address 36
[17179640.620000] usb 4-8: new high speed USB device using ehci_hcd and address 39

```

There is no mention of sda under /dev, either.
The drive works perfectly in WinXP and on other Win machines, also.

Anyone have any suggestions or other tests I could try?:confused:

---

### Post by mchatel on 2007-02-09
I hope someone is able to help you on this forum, with your Memorex TravelDrive problem.  I just thought I'd share some encouraging news.... I have a Memorex TravelDrive (with U3).  It's the 2GB one.  And it works just fine on my system.  So, I'm sure it's just a setting on your specific system or something.  I wondered if it would work, but it worked without any intervention from me at all.  (I haven't tried using the U3 features of it), but it works as a regular thumb-drive just fine.

Hopefully someone with the technical know-how can offer you some helpful advice.  :-)

---

### Post by JLuv on 2007-02-09
I hope someone helps, also. 

I know it will work with Ubuntu, it worked yesterday when I first installed 6.10. But then it suddenly stopped working after a few hours. 

Thanks for the encouragement.

---

### Post by JLuv on 2007-02-09
Now my iPod isn't being recognized!! :confused: :(

[edit]My iPod works now. I just rebooted. [/edit]

---

### Post by JLuv on 2007-02-09
BUMP

And here is what i get from dmesg | grep --i usb

```
[17179638.008000] usb 4-8: new high speed USB device using ehci_hcd and address 32
[17179638.140000] usb 4-8: configuration #1 chosen from 2 choices
[17179638.256000] usbcore: registered new driver libusual
[17179638.332000] Initializing USB Mass Storage driver...
[17179638.332000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179638.332000] usbcore: registered new driver usb-storage
[17179638.332000] USB Mass Storage support registered.
[17179638.332000] usb-storage: device found at 32
[17179638.332000] usb-storage: waiting for device to settle before scanning
[17179643.332000] usb-storage: device scan complete
[17179926.812000] usb 4-8: USB disconnect, address 32
[17179947.464000] usb 4-8: new high speed USB device using ehci_hcd and address 36
[17179950.992000] usb 4-8: new high speed USB device using ehci_hcd and address 47
[17179952.252000] usb 4-8: new high speed USB device using ehci_hcd and address 51
[17179954.268000] usb 4-8: new high speed USB device using ehci_hcd and address 58
[17179955.024000] usb 4-8: new high speed USB device using ehci_hcd and address 60
[17179955.528000] usb 4-8: new high speed USB device using ehci_hcd and address 61
[17179957.796000] usb 4-8: new high speed USB device using ehci_hcd and address 69
[17179958.300000] usb 4-8: new high speed USB device using ehci_hcd and address 70
[17179958.804000] usb 4-8: new high speed USB device using ehci_hcd and address 71
[17179959.676000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17179963.340000] usb 4-8: new high speed USB device using ehci_hcd and address 83
[17179964.600000] usb 4-8: new high speed USB device using ehci_hcd and address 85
[17179966.112000] usb 4-8: new high speed USB device using ehci_hcd and address 88
[17179968.632000] usb 4-8: new high speed USB device using ehci_hcd and address 97
[17179969.388000] usb 4-8: new high speed USB device using ehci_hcd and address 99
[17179971.152000] usb 4-8: new high speed USB device using ehci_hcd and address 105
[17179971.908000] usb 4-8: new high speed USB device using ehci_hcd and address 107
[17179973.168000] usb 4-8: new high speed USB device using ehci_hcd and address 111
[17179975.688000] usb 4-8: new high speed USB device using ehci_hcd and address 120
[17179978.208000] usb 4-8: new high speed USB device using ehci_hcd and address 3
[17179978.964000] usb 4-8: new high speed USB device using ehci_hcd and address 5
[17179979.972000] usb 4-8: new high speed USB device using ehci_hcd and address 6
[17179980.476000] usb 4-8: new high speed USB device using ehci_hcd and address 7
[17179982.492000] usb 4-8: new high speed USB device using ehci_hcd and address 14
[17179983.752000] usb 4-8: new high speed USB device using ehci_hcd and address 18
[17179985.264000] usb 4-8: new high speed USB device using ehci_hcd and address 23
[17179985.768000] usb 4-8: new high speed USB device using ehci_hcd and address 24
[17179987.532000] usb 4-8: new high speed USB device using ehci_hcd and address 28
[17179988.540000] usb 4-8: new high speed USB device using ehci_hcd and address 29
[17179990.052000] usb 4-8: new high speed USB device using ehci_hcd and address 34
[17179990.808000] usb 4-8: new high speed USB device using ehci_hcd and address 36
[17179992.068000] usb 4-8: new high speed USB device using ehci_hcd and address 38
[17179992.940000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17179994.588000] usb 4-8: new high speed USB device using ehci_hcd and address 44
[17179995.848000] usb 4-8: new high speed USB device using ehci_hcd and address 48
[17179998.116000] usb 4-8: new high speed USB device using ehci_hcd and address 54
[17179999.628000] usb 4-8: new high speed USB device using ehci_hcd and address 59
[17180001.896000] usb 4-8: new high speed USB device using ehci_hcd and address 65
[17180002.400000] usb 4-8: new high speed USB device using ehci_hcd and address 66
[17180003.156000] usb 4-8: new high speed USB device using ehci_hcd and address 68
[17180004.164000] usb 4-8: new high speed USB device using ehci_hcd and address 71
[17180005.172000] usb 4-8: new high speed USB device using ehci_hcd and address 72
[17180006.936000] usb 4-8: new high speed USB device using ehci_hcd and address 78
[17180009.708000] usb 4-8: new high speed USB device using ehci_hcd and address 86
[17180010.580000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180012.984000] usb 4-8: new high speed USB device using ehci_hcd and address 95
[17180013.992000] usb 4-8: new high speed USB device using ehci_hcd and address 98
[17180014.864000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180017.520000] usb 4-8: new high speed USB device using ehci_hcd and address 108
[17180018.276000] usb 4-8: new high speed USB device using ehci_hcd and address 110
[17180018.780000] usb 4-8: new high speed USB device using ehci_hcd and address 111
[17180019.788000] usb 4-8: new high speed USB device using ehci_hcd and address 114
[17180020.544000] usb 4-8: new high speed USB device using ehci_hcd and address 116
[17180021.048000] usb 4-8: new high speed USB device using ehci_hcd and address 117
[17180021.552000] usb 4-8: new high speed USB device using ehci_hcd and address 118
[17180022.560000] usb 4-8: new high speed USB device using ehci_hcd and address 121
[17180023.568000] usb 4-8: new high speed USB device using ehci_hcd and address 124
[17180024.072000] usb 4-8: new high speed USB device using ehci_hcd and address 125
[17180024.576000] usb 4-8: new high speed USB device using ehci_hcd and address 126
[17180025.080000] usb 4-8: new high speed USB device using ehci_hcd and address 127
[17180025.836000] usb 4-8: new high speed USB device using ehci_hcd and address 3
[17180026.340000] usb 4-8: new high speed USB device using ehci_hcd and address 4
[17180026.844000] usb 4-8: new high speed USB device using ehci_hcd and address 5
[17180028.104000] usb 4-8: new high speed USB device using ehci_hcd and address 9
[17180028.976000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180029.616000] usb 4-8: new high speed USB device using ehci_hcd and address 11
[17180030.876000] usb 4-8: new high speed USB device using ehci_hcd and address 13
[17180032.136000] usb 4-8: new high speed USB device using ehci_hcd and address 17
[17180032.892000] usb 4-8: new high speed USB device using ehci_hcd and address 19
[17180034.152000] usb 4-8: new high speed USB device using ehci_hcd and address 23
[17180035.412000] usb 4-8: new high speed USB device using ehci_hcd and address 25
[17180038.436000] usb 4-8: new high speed USB device using ehci_hcd and address 36
[17180038.940000] usb 4-8: new high speed USB device using ehci_hcd and address 37
[17180039.444000] usb 4-8: new high speed USB device using ehci_hcd and address 38
[17180040.200000] usb 4-8: new high speed USB device using ehci_hcd and address 40
[17180041.072000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180042.972000] usb 4-8: new high speed USB device using ehci_hcd and address 47
[17180043.844000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180044.484000] usb 4-8: new high speed USB device using ehci_hcd and address 49
[17180048.768000] usb 4-8: new high speed USB device using ehci_hcd and address 65
[17180049.272000] usb 4-8: new high speed USB device using ehci_hcd and address 66
[17180052.548000] usb 4-8: new high speed USB device using ehci_hcd and address 78
[17180053.556000] usb 4-8: new high speed USB device using ehci_hcd and address 81
[17180055.320000] usb 4-8: new high speed USB device using ehci_hcd and address 87
[17180057.336000] usb 4-8: new high speed USB device using ehci_hcd and address 92
[17180058.344000] usb 4-8: new high speed USB device using ehci_hcd and address 95
[17180059.856000] usb 4-8: new high speed USB device using ehci_hcd and address 100
[17180061.368000] usb 4-8: new high speed USB device using ehci_hcd and address 103
[17180061.872000] usb 4-8: new high speed USB device using ehci_hcd and address 104
[17180062.376000] usb 4-8: new high speed USB device using ehci_hcd and address 105
[17180063.384000] usb 4-8: new high speed USB device using ehci_hcd and address 108
[17180064.140000] usb 4-8: new high speed USB device using ehci_hcd and address 110
[17180064.896000] usb 4-8: new high speed USB device using ehci_hcd and address 112
[17180065.652000] usb 4-8: new high speed USB device using ehci_hcd and address 114
[17180066.524000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180067.396000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180068.268000] hub 4-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[17180069.048000] usb 4-8: new high speed USB device using ehci_hcd and address 117
[17180069.456000] usb 4-8: device not accepting address 117, error -71
```

I think the problem lies in the very last line. I've searched Google but can't find a solution. Seems like all the threads that attempt this problem just die off. :/

---

### Post by justin whitaker on 2007-02-12
I'm having the same issue with Ubuntu, but not with Sabayon. That means it is something specific to Ubuntu, the kernel, or how HAL handles USB. 

Right now, my iPod, my Memorex Traveldrive, and my Maxtor External drive might as well be paperweights as far as Ubuntu is concerned. 

Annoying.

---

### Post by JLuv on 2007-02-17
So, apparently, my thumb drive decides to work today.

I swear I didn't change anyhing. I just rebooted from WinXP to Ubuntu (which i've done numerous times before) and it worked.

---

### Post by sb73542 on 2007-08-20
Same thing here, it occasionally hotplugs or coldplugs but not usually.  This is crazy.  Typical Ubuntu hassle.

---

### Post by Aholiab on 2008-02-13
I just got a 8 Gb Memorex TravelDrive, and I'm running Gutsy. This flash stick seems to never mount when I insert it, so I pull it out and re-insert it, and it mounts just fine and dandy. No clue why this is.

---

