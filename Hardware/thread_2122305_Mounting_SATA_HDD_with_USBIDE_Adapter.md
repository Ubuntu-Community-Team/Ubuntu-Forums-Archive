---
title: "Mounting SATA HDD with USB/IDE Adapter"
date: 2013-03-04
forum: Hardware
---

### Post by smc18 on 2013-03-04
**EDIT Problem Solved.  (It seems the "Solved" button is no longer part of the forums... it's been a long time.)

Hey guys

I have a Samsung 1TB SATA drive hooked up to a USB->IDE/SATA Adapter ([Similiar to what's shown here]("http://www.amazon.com/s/ref=nb_sb_ss_i_0_7?url=search-alias%3Daps&field-keywords=usb+ide+sata+adapter&sprefix=usb+ide%2Caps%2C184")).  When I plug it in, it's not listed in fdisk.  I would like to backup some files to this external HDD.  It has been formatted with NTFS.  There is only one partition on it.


I've done some searching and most people come back with these results, but I can't find a good solution.

```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f470

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          121419      121601     1469947+   5  Extended
/dev/sda2               1        1277    10257471   83  Linux
/dev/sda4            1278      121418   965032582+  fd  Linux raid autodetect
/dev/sda5          121420      121601     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a3a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          121419      121601     1469947+   5  Extended
/dev/sdb2   *           1        1216     9767488+  83  Linux
/dev/sdb3            1217        1277      489982+  83  Linux
/dev/sdb4            1278      121418   965032582+  fd  Linux raid autodetect
/dev/sdb5          121420      121601     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
tail -f /var/log/messages

Mar  4 12:27:20 xxxxx kernel: [4442174.869420] sd 2:0:0:0: [sdc] Attached SCSI disk
Mar  4 12:27:20 xxxxx kernel: [4442174.869656] sd 2:0:0:0: Attached scsi generic sg3 type 0
Mar  4 12:51:42 xxxxx -- MARK --
Mar  4 13:11:23 xxxxx kernel: [4444817.710374] usb 1-2: USB disconnect, address 2
Mar  4 13:11:51 xxxxx kernel: [4444845.690023] usb 1-1: new high speed USB device using ehci_hcd and address 3
Mar  4 13:11:51 xxxxx kernel: [4444845.842087] usb 1-1: configuration #1 chosen from 1 choice
Mar  4 13:11:51 xxxxx kernel: [4444845.843443] scsi3 : SCSI emulation for USB Mass Storage devices
Mar  4 13:11:56 xxxxx kernel: [4444850.841429] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Mar  4 13:11:56 xxxxx kernel: [4444850.864180] sd 3:0:0:0: [sdc] Attached SCSI disk
Mar  4 13:11:56 xxxxx kernel: [4444850.864427] sd 3:0:0:0: Attached scsi generic sg3 type 0

```

```
dmesg

[4442169.590021] usb 1-2: new high speed USB device using ehci_hcd and address 2
[4442169.742142] usb 1-2: configuration #1 chosen from 1 choice
[4442169.836704] usbcore: registered new interface driver libusual
[4442169.863686] Initializing USB Mass Storage driver...
[4442169.863820] scsi2 : SCSI emulation for USB Mass Storage devices
[4442169.863973] usbcore: registered new interface driver usb-storage
[4442169.863980] USB Mass Storage support registered.
[4442169.868491] usb-storage: device found at 2
[4442169.868497] usb-storage: waiting for device to settle before scanning
[4442174.860252] usb-storage: device scan complete
[4442174.861464] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[4442174.869420] sd 2:0:0:0: [sdc] Attached SCSI disk
[4442174.869656] sd 2:0:0:0: Attached scsi generic sg3 type 0
[4444817.710374] usb 1-2: USB disconnect, address 2
[4444845.690023] usb 1-1: new high speed USB device using ehci_hcd and address 3
[4444845.842087] usb 1-1: configuration #1 chosen from 1 choice
[4444845.843443] scsi3 : SCSI emulation for USB Mass Storage devices
[4444845.843575] usb-storage: device found at 3
[4444845.843578] usb-storage: waiting for device to settle before scanning
[4444850.840226] usb-storage: device scan complete
[4444850.841429] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[4444850.864180] sd 3:0:0:0: [sdc] Attached SCSI disk
[4444850.864427] sd 3:0:0:0: Attached scsi generic sg3 type 0

```


```

lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
sudo fdisk /dev/sdc

Unable to read /dev/sdc

```

```
sudo uname -r
2.6.27-16-server

```


[This thread]("http://ubuntuforums.org/showthread.php?t=928820&highlight=Mount+SATA+USB+Adapter") seems to be very identical, except I'm using the server version and not the desktop version.

Any help on how to properly mount this drive?

If I'm missing any information, please ask for it. :) Thanks!!

---

### Post by smc18 on 2013-03-04
Here's some more info about the disks.  (Remember I'm only having a problem with my external USB SATA/IDE Adapter.  It looks like it's suppose to b

```
sudo mount /dev/sdc1 /mnt/external -t ntfs -o nls=utf8,umask=0222

ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```

**As we see below, there is no /dev/sdc1 (As mentioned in the first post, this HDD should have a single NTFS partition created in Windows)

```
ls /dev/sd*

/dev/sda   /dev/sda2  /dev/sda5  /dev/sdb1  /dev/sdb3  /dev/sdb5
/dev/sda1  /dev/sda4  /dev/sdb   /dev/sdb2  /dev/sdb4  /dev/sdc
```

```
sudo lshw
...
     *-disk:0
                description: ATA Disk
                product: WDC WD10EADS-00L
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-xxxxxxxx
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002f470
...
     *-disk:1
                description: ATA Disk
                product: WDC WD10EADS-00L
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-xxxxxxxx
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001a3a1
...

     *-scsi
          physical id: 1
          bus info: usb@1:1
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc


```

---

### Post by smc18 on 2013-03-04
After rebooting and running fdisk again this is what I get:

```
sudo fdisk -l
...
...
Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75207520

Disk /dev/sdc doesn't contain a valid partition table

```

weird thing is, this ia 1TB drive, not a 2TB drive.

---

### Post by smc18 on 2013-03-04
I feel like I'm posting too much now... but I keep reading and trying new things, so I figured I will keep the updates coming.

after reading some other suggestions, I tried reformatting the drive (after procedding a warning - sorry I didn't record it or the format summary).

```
sudo mkfs -t ext3 /dev/sdc
```

Afterwards /dev/sdc no longer exists and I check dmesg

```
dmesg
...

[ 7475.302595] Buffer I/O error on device sdc, logical block 476774818
[ 7475.302618] lost page write due to I/O error on sdc
[ 7480.313094] __ratelimit: 458735 callbacks suppressed
[ 7480.313106] Buffer I/O error on device sdc, logical block 506134930
[ 7480.313137] lost page write due to I/O error on sdc
[ 7480.313146] Buffer I/O error on device sdc, logical block 506134931
[ 7480.313169] lost page write due to I/O error on sdc
[ 7480.313174] Buffer I/O error on device sdc, logical block 506134932
[ 7480.313197] lost page write due to I/O error on sdc
[ 7480.313202] Buffer I/O error on device sdc, logical block 506134933
[ 7480.313225] lost page write due to I/O error on sdc
[ 7480.313230] Buffer I/O error on device sdc, logical block 506134934
[ 7480.313253] lost page write due to I/O error on sdc
[ 7480.313257] Buffer I/O error on device sdc, logical block 506134935
[ 7480.313280] lost page write due to I/O error on sdc
[ 7480.313285] Buffer I/O error on device sdc, logical block 506134936
[ 7480.313308] lost page write due to I/O error on sdc
[ 7480.313312] Buffer I/O error on device sdc, logical block 506134937
[ 7480.313335] lost page write due to I/O error on sdc
[ 7480.313340] Buffer I/O error on device sdc, logical block 506134938
[ 7480.313363] lost page write due to I/O error on sdc
[ 7480.313367] Buffer I/O error on device sdc, logical block 506134939
[ 7480.313390] lost page write due to I/O error on sdc
[ 7485.320063] __ratelimit: 456628 callbacks suppressed
[ 7485.320074] Buffer I/O error on device sdc, logical block 535363920
[ 7485.320105] lost page write due to I/O error on sdc
[ 7485.320113] Buffer I/O error on device sdc, logical block 535363921
[ 7485.320137] lost page write due to I/O error on sdc
[ 7485.320141] Buffer I/O error on device sdc, logical block 535363922
[ 7485.320165] lost page write due to I/O error on sdc
[ 7485.320170] Buffer I/O error on device sdc, logical block 535363923
[ 7485.320193] lost page write due to I/O error on sdc


```

Weird... What is going on? I doubt the drive is going bad; I've had it for about a year and it's only been in use for 2/3 months for testing purposes.  Plus, it was working fine on my Windows box today.  (I suppose I shouldn't rule it out though)

---

### Post by sudodus on 2013-03-05
I have a similar device to connect IDE (PATA) as well as SATA devices via USB. And it works properly for me.

- Have you managed to connect another drive via this device?

- Have you managed to connect this drive internally to a computer (it would be easiest with a desktop PC or workstation)?

- Have you managed to connect another USB device, for example a flash pendrive to the same USB port of your computer?

- Have you tried if the drive is recognized with parted or gparted? These programs might need to be installed.

```
sudo parted -l
```

```
gksudo gparted
```

---

### Post by smc18 on 2013-03-05
> - Have you managed to connect another drive via this device?

Here is with a 80GB IDE Drive hooked up to the USB to SATA/IDE Adapter
```
sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f470

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          121419      121601     1469947+   5  Extended
/dev/sda2               1        1277    10257471   83  Linux
/dev/sda4            1278      121418   965032582+  fd  Linux raid autodetect
/dev/sda5          121420      121601     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a3a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          121419      121601     1469947+   5  Extended
/dev/sdb2   *           1        1216     9767488+  83  Linux
/dev/sdb3            1217        1277      489982+  83  Linux
/dev/sdb4            1278      121418   965032582+  fd  Linux raid autodetect
/dev/sdb5          121420      121601     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 8006 MB, 8006926336 bytes
247 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      210559      238826   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(210558, 221, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(238825, 64, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      213663      341223   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(213662, 17, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(60762, 71, 9)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?           1           1           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(280460, 46, 4)
Partition 3 does not end on cylinder boundary.
/dev/sdc4            3279       63637   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(3278, 20, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(63636, 236, 34)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
128 heads, 63 sectors/track, 19382 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0xf95cb0ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19382    78148192+   7  HPFS/NTFS

```

/dev/sdc is a 8GB Thumb Drive
/dev/sdd is my 80GB IDE Drive w/adapter     **I've been able to mount and browse this drive fine.


> - Have you managed to connect this drive internally to a computer (it would be easiest with a desktop PC or workstation)?

I've used the 1TB SATA HDD in another build as an internal drive.  I've the drive sitting to the side, and yesteryday I reformatted it in Windows with the USB adapter, then tried plugging it into this box.

> - Have you managed to connect another USB device, for example a flash pendrive to the same USB port of your computer?

In the sample above, shows a thumb drive plugged into the same USB port as I was trying yesterday.  Today I plugged an IDE Drive with the USB adapter in a separate port right above the last.

> - Have you tried if the drive is recognized with parted or gparted? These programs might need to be installed.

I haven't tried using parted or gparted.  Before I try that, I'm going to reformat the 1TB drive and try again. (Thanks for the suggestion, sorry for not trying it just yet :D)

---

### Post by smc18 on 2013-03-05
Ughh frustrating... I reconnected the SATA drive to the linux box and reformatted the SATA drive as FAT32. Worked fine. Mounted and created a test file, removed the drive and hooked it up to a Windows box and it was recognized with my test file.  I then reformatted to NTFS, created a new test file, hooked it up to the linux box I needed it for, and it reads it fine.

I'm going to blame this on either a bad format, or I'd hate to admit... a loose cable when I initially had everything hooked up.  Problem potentially solved.

---

### Post by sudodus on 2013-03-06
I'm glad it works for you now to mount your SATA HDD with the USB/IDE Adapter :-)

This new software for the Ubuntu Forums needs some tweaking, but it should be possible to mark the thread as SOLVED, if you edit your first post, go into advanced mode, and type SOLVED into a small editing space above the space for the main text. (At least it worked a couple of days ago.)

---

