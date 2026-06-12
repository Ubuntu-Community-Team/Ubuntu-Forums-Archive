---
title: "USB Stick Faulty?"
date: 2010-05-31
forum: Hardware
---

### Post by Lord Stig on 2010-05-31
I recently won an auction on a world famous auction site for a tiny 32GB USB flash drive. The drive is one of those really small thin ones which slides into rather than over the USB port.

When I plugged it in it didn't appear to be formatted. In Lucid Lynx I went to Disk Utility and the drive appeared as a 2.2TB (!!) capacity drive with a description beneath of 0000 0000.
I booted Windows XP to see what it would make of it and it detected the new hardware but said it couldn't install the drivers for it. It appears in My Computer as a Removable Disk but when I try to open it I get the message that the drive is not formatted. It prompts me to format it but thinks the capacity is only 8MB and only lists FAT as the file system.

I booted back into Lucid, having NOT formatted it, and Disk Utility and tried to format it using Format Volume as NTFS (in case I use it in Windows). This failed with the message:
<CODE>Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error</CODE>
Disk Utility now thinks it has an 8.4MB capacity and fails the format in ext4 and FAT with the same error message. I tried Format Drive and the options are unfamiliar to me, save for Master Boot Record but I don't think I need that for a USB drive?

Can anyone help? The drive was very cheap and I'm wondering if it's a dud or a fake.

---

### Post by arrange on 2010-05-31
Plug the stick in and after a few seconds provide the output of```
sudo fdisk -lu
dmesg | tail -20

```

---

### Post by Lord Stig on 2010-05-31
> **arrange said:**
> Plug the stick in and after a few seconds provide the output of```
sudo fdisk -lu
dmesg | tail -20

```

Thanks for the quick reply.

```

carl@carl-desktop:~$ sudo fdisk -lu
[sudo] password for carl: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c24c74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38218634    19109286    7  HPFS/NTFS
/dev/sda2        38218759   156296384    59038813    5  Extended
/dev/sda5       124327098   154866599    15269751   83  Linux
/dev/sda6       154866663   156296384      714861   82  Linux swap / Solaris
/dev/sda7        76726566   122254649    22764042   83  Linux
/dev/sda8       122254713   124327034     1036161   82  Linux swap / Solaris
/dev/sda9        38218761    75023549    18402394+  83  Linux
/dev/sda10       75023613    76726439      851413+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2015230     1007584    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

Disk /dev/sdc: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
carl@carl-desktop:~$ dmesg | tail -20
[ 3410.196021] usb 6-2: device not accepting address 17, error -62
[ 3410.332032] usb 6-2: new full speed USB device using ohci_hcd and address 18
[ 3415.740036] usb 6-2: device not accepting address 18, error -62
[ 3415.740087] hub 6-0:1.0: unable to enumerate USB device on port 2
[ 6558.916038] usb 1-10: new high speed USB device using ehci_hcd and address 41
[ 6559.048587] usb 1-10: configuration #1 chosen from 1 choice
[ 6559.048966] scsi18 : SCSI emulation for USB Mass Storage devices
[ 6559.049216] usb-storage: device found at 41
[ 6559.049219] usb-storage: waiting for device to settle before scanning
[ 6564.048268] usb-storage: device scan complete
[ 6564.048729] scsi 18:0:0:0: Direct-Access     ChipsBnk Flash Disk       5.00 PQ: 0 ANSI: 2
[ 6564.058945] sd 18:0:0:0: [sdc] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[ 6564.060231] sd 18:0:0:0: [sdc] Write Protect is off
[ 6564.060238] sd 18:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 6564.060243] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.062941] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.062955]  sdc: unknown partition table
[ 6564.064899] sd 18:0:0:0: Attached scsi generic sg3 type 0
[ 6564.068950] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.068960] sd 18:0:0:0: [sdc] Attached SCSI removable disk
carl@carl-desktop:~$ ^C
carl@carl-desktop:~$ 
0*$ shell                                 carl@carl-desktop 10.0.0.101 Menu:<F9>
 U  Ubuntu 10.04          23!  1h50m 0.58 2x2.8GHz 1.3GB,18% 2010-05-31 22:00:28
/dev/sda5       124327098   154866599    15269751   83  Linux
/dev/sda6       154866663   156296384      714861   82  Linux swap / Solaris
/dev/sda7        76726566   122254649    22764042   83  Linux
/dev/sda8       122254713   124327034     1036161   82  Linux swap / Solaris
/dev/sda9        38218761    75023549    18402394+  83  Linux
/dev/sda10       75023613    76726439      851413+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2015230     1007584    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

Disk /dev/sdc: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
carl@carl-desktop:~$ dmesg | tail -20
[ 3410.196021] usb 6-2: device not accepting address 17, error -62
[ 3410.332032] usb 6-2: new full speed USB device using ohci_hcd and address 18
[ 3415.740036] usb 6-2: device not accepting address 18, error -62
[ 3415.740087] hub 6-0:1.0: unable to enumerate USB device on port 2
[ 6558.916038] usb 1-10: new high speed USB device using ehci_hcd and address 41
[ 6559.048587] usb 1-10: configuration #1 chosen from 1 choice
[ 6559.048966] scsi18 : SCSI emulation for USB Mass Storage devices
[ 6559.049216] usb-storage: device found at 41
[ 6559.049219] usb-storage: waiting for device to settle before scanning
[ 6564.048268] usb-storage: device scan complete
[ 6564.048729] scsi 18:0:0:0: Direct-Access     ChipsBnk Flash Disk       5.00 PQ: 0 ANSI: 2
[ 6564.058945] sd 18:0:0:0: [sdc] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[ 6564.060231] sd 18:0:0:0: [sdc] Write Protect is off
[ 6564.060238] sd 18:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 6564.060243] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.062941] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.062955]  sdc: unknown partition table
[ 6564.064899] sd 18:0:0:0: Attached scsi generic sg3 type 0
[ 6564.068950] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6564.068960] sd 18:0:0:0: [sdc] Attached SCSI removable disk

```
There was another memory stick plugged in at the time I did these instructions; I believe the device you're looking for is sdc1 (it is according to Disk Utility)

---

### Post by arrange on 2010-05-31
[COLOR="Silver"] 6564.058945] sd 18:0:0:0: [sdc] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[/COLOR]I hope someone will prove me wrong, but if the kernel reports 8 MiB, I think you won't be able to go any further than that :(

---

### Post by Lord Stig on 2010-05-31
> **arrange said:**
> [COLOR="Silver"] 6564.058945] sd 18:0:0:0: [sdc] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[/COLOR]I hope someone will prove me wrong, but if the kernel reports 8 MiB, I think you won't be able to go any further than that :(

I hope not! Attempting to partition it as GUID returns the capacity to an indicated 2.2GB. Then, trying to format it, it runs for longer before producing the same error message.

Please, can anyone help?

---

### Post by arrange on 2010-05-31
Seems to be a common issue with this flash drive. Google *ChipsBnk Flash Disk*, f.e. [http://help.com/post/56531-my-1g-chipsbnk-usb-drive-is-listed](http://help.com/post/56531-my-1g-chipsbnk-usb-drive-is-listed)

---

### Post by seadao on 2010-06-12
same issue on ubuntu 10.04 but using an sd card

the sd card doesn't mount in ubuntu, but mounts and reads fine in windows 7
this card has worked with ubuntu for the last 3 years prior to this

---

