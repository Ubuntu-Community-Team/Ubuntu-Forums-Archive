---
title: "External WD HD not working correctly"
date: 2012-08-02
forum: Hardware
---

### Post by Paww on 2012-08-02
I have a problem regarding my external drive, a 1TB MyBook Essential (the one with the 3.0 usb). Sometimes it is not detected at as a drive.

It has a single ext3 partition.

In the beginning it was like this:

lsusb shows the drive:
```
[pawbla@arch-laptop ~]$ lsusb
[..]
Bus 002 Device 005: ID 1058:1130 Western Digital Technologies, Inc. 
[..]

```
And a parted -l
```
[pawbla@arch-laptop ~]$ sudo parted -l
Password: 
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  206MB   206MB   primary   ntfs            boot
 2      206MB   84.2GB  84.0GB  primary   ntfs
 3      84.2GB  84.7GB  510MB   primary   ext2
 4      84.7GB  500GB   415GB   extended
 5      84.7GB  89.7GB  5001MB  logical   linux-swap(v1)
 6      89.7GB  122GB   32.6GB  logical   ext3
 7      122GB   500GB   378GB   logical   ext3


Error: Error opening /dev/sdb: No such file or directory
Retry/Cancel? C
Model: /6:0:0:0  (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

```
This makes me think the disk is not (still) fried, but maybe it has FS problem? Maybe it was not cleanly unmounted or something, I don't know if that would cause this.

If I tried to do another parted -l it skippped the external hard drive.


Then I managed to mount it:

```
[34859.424851] usb 2-1.1: new high-speed USB device number 6 using ehci_hcd
[34860.166392] scsi7 : usb-storage 2-1.1:1.0
[34862.238147] scsi 7:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[34868.148776] scsi 7:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6

```

So I found out that, in Windows, the drive appeared to be locked. I never locked it or set a password for it.

Complete parted -l with working drive:
```
Model: WD My Book 1130 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext3

```

Then it locked itself again.
Dmesg:
```
[  291.400196] usb 2-1.1: new high-speed USB device number 5 using ehci_hcd
[  292.219909] usbcore: registered new interface driver uas
[  292.225899] Initializing USB Mass Storage driver...
[  292.226167] scsi6 : usb-storage 2-1.1:1.0
[  292.226406] usbcore: registered new interface driver usb-storage
[  292.226411] USB Mass Storage support registered.
[  294.214506] scsi 6:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[  300.215099] scsi 6:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[  314.190482] sd 6:0:0:0: [sdb] Spinning up disk...
[  344.961238] usb 2-1.1: reset high-speed USB device number 5 using ehci_hcd
[...]
[  389.977053] usb 2-1.1: reset high-speed USB device number 5 using ehci_hcd
[...]
[  434.806407] usb 2-1.1: reset high-speed USB device number 5 using ehci_hcd
```

Two weeks later, after my holidays, I got back to trying and got a different message:

```
[  421.602537] usb 2-1.1: new high-speed USB device number 5 using ehci_hcd
[  421.862619] hub 2-1:1.0: unable to enumerate USB device on port 1
[  423.106565] usb 2-1.1: new high-speed USB device number 6 using ehci_hcd
[  424.200173] usbcore: registered new interface driver uas
[  424.205138] Initializing USB Mass Storage driver...
[  424.205359] scsi6 : usb-storage 2-1.1:1.0
[  424.205588] usbcore: registered new interface driver usb-storage
[  424.205592] USB Mass Storage support registered.
[  426.996556] scsi 6:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[  426.998848] scsi 6:0:0:1: CD-ROM            WD       Virtual CD 1130  1012 PQ: 0 ANSI: 6
[  427.002125] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  427.003183] sr1: scsi-1 drive
[  427.003749] sr 6:0:0:1: Attached scsi CD-ROM sr1
[  427.004178] sd 6:0:0:0: [sdb] Asking for cache data failed
[  427.004187] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  427.007349] scsi 6:0:0:2: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[  427.014675] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  427.017426] sd 6:0:0:0: [sdb] Asking for cache data failed
[  427.017437] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  427.017446] sd 6:0:0:0: [sdb] Attached SCSI disk
[  427.112260] scsi 6:0:0:2: Failed to get diagnostic page 0x8000002
[  427.112264] scsi 6:0:0:2: Failed to bind enclosure -19
[  427.112280] ses 6:0:0:2: Attached Enclosure device
[  725.759130] usb 2-1.1: USB disconnect, device number 6
[  727.252427] usb 2-1.1: new high-speed USB device number 7 using ehci_hcd
[  727.993616] scsi7 : usb-storage 2-1.1:1.0
[  731.142461] scsi 7:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[  731.144438] scsi 7:0:0:1: CD-ROM            WD       Virtual CD 1130  1012 PQ: 0 ANSI: 6
[  731.147161] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  731.148166] sr1: scsi-1 drive
[  731.149321] sd 7:0:0:0: [sdb] Asking for cache data failed
[  731.149330] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  731.149743] sr 7:0:0:1: Attached scsi CD-ROM sr1
[  731.152298] scsi 7:0:0:2: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[  731.154375] ses 7:0:0:2: Attached Enclosure device
[  731.155004] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  731.156016] ses 7:0:0:2: Failed to get diagnostic page 0x8000002
[  731.156028] ses 7:0:0:2: Failed to bind enclosure -19
[  731.157036] sd 7:0:0:0: [sdb] Asking for cache data failed
[  731.157043] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  731.157048] sd 7:0:0:0: [sdb] Attached SCSI disk
```

The drive does not show up as locked anymore.

Thoughts?

Thanks a lot for your answers.

---

### Post by Paww on 2012-08-03
Also I believe the drive died after an unexpected shutdown.

---

