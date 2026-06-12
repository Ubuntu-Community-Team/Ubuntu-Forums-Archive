---
title: "USB storage not recognized in I version of Ubuntu"
date: 2009-04-14
forum: Hardware
---

### Post by flyingfree on 2009-04-14
I have tried a few USBdevices on my computer and none of them are recognized. any ideas of how I can fix this problem?

---

### Post by ddrichardson on 2009-04-15
No without a lot more information - if you insert a device and enter```
dmesg
```in a terminal, does it say anything about USB?

Some PC's, especially HP, need to be booted with specific kernel options - the ones needed for the TX series are on [my wiki]("http://wiki.lynxworks.eu/ubuntu/tx1250ea#booting_the_live_cd"), it might be worth trying them.

---

### Post by flyingfree on 2009-04-21
> **ddrichardson said:**
> No without a lot more information - if you insert a device and enter```
dmesg
```in a terminal, does it say anything about USB?

Some PC's, especially HP, need to be booted with specific kernel options - the ones needed for the TX series are on [my wiki]("http://wiki.lynxworks.eu/ubuntu/tx1250ea#booting_the_live_cd"), it might be worth trying them.

Thanks for the help sorry for the late reply, lost my interenet for a while.  dmesg with a simple key chain digital photoframe looks like this minus all the entries about my wlan.

[107768.064033] usb 1-1: new full speed USB device using uhci_hcd and address 5
[107768.269713] usb 1-1: configuration #1 chosen from 1 choice
[107768.288846] scsi3 : SCSI emulation for USB Mass Storage devices
[107768.290803] usb-storage: device found at 5
[107768.290811] usb-storage: waiting for device to settle before scanning
[107773.290050] usb-storage: device scan complete
[107773.293011] scsi 3:0:0:0: Direct-Access     SITRONIX MULTIMEDIA       0.09 PQ: 0 ANSI: 0 CCS
[107773.308987] sd 3:0:0:0: [sdb] 4096 512-byte hardware sectors (2 MB)
[107773.311984] sd 3:0:0:0: [sdb] Write Protect is off
[107773.311990] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[107773.311994] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[107773.333225] sd 3:0:0:0: [sdb] 4096 512-byte hardware sectors (2 MB)
[107773.341064] sd 3:0:0:0: [sdb] Write Protect is off
[107773.341075] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[107773.341079] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[107773.341740]  sdb: unknown partition table
[107773.367146] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[107773.368158] sd 3:0:0:0: Attached scsi generic sg2 type 0


Also wondering why it will not allow me to view the contents of any of the other partitions on my hard drive?  Wondering if the inability to mount drives is part of the problem.

---

### Post by flyingfree on 2009-04-25
Still struggling with this problem.

---

### Post by ddrichardson on 2009-04-25
When plugged in, what's the output of```
sudo fdisk -l
```

---

### Post by compeng on 2009-10-16
I am having the same problem.
> **ddrichardson said:**
> When plugged in, what's the output of```
sudo fdisk -l
```
Output of fdisk -l
```
Disk /dev/sdg: 2 MB, 2097152 bytes
1 heads, 4 sectors/track, 1024 cylinders
Units = cylinders of 4 * 512 = 2048 bytes
Disk identifier: 0x0371ad60

Disk /dev/sdg doesn't contain a valid partition table

```My dmesg output is 
```
[ 1408.313555] usb 6-1: new full speed USB device using ohci_hcd and address 4
[ 1408.480693] usb 6-1: configuration #1 chosen from 1 choice
[ 1408.482469] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1408.482761] usb-storage: device found at 4
[ 1408.482768] usb-storage: waiting for device to settle before scanning
[ 1413.480718] usb-storage: device scan complete
[ 1413.486674] scsi 9:0:0:0: Direct-Access     SITRONIX MULTIMEDIA       0.09 PQ: 0 ANSI: 0 CCS
[ 1413.501655] sd 9:0:0:0: [sdg] 4096 512-byte hardware sectors: (2.09 MB/2.00 MiB)
[ 1413.508057] sd 9:0:0:0: [sdg] Write Protect is off
[ 1413.508066] sd 9:0:0:0: [sdg] Mode Sense: 0b 00 00 08
[ 1413.508071] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 1413.526651] sd 9:0:0:0: [sdg] 4096 512-byte hardware sectors: (2.09 MB/2.00 MiB)
[ 1413.532649] sd 9:0:0:0: [sdg] Write Protect is off
[ 1413.532656] sd 9:0:0:0: [sdg] Mode Sense: 0b 00 00 08
[ 1413.532661] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 1413.532670]  sdg: unknown partition table
[ 1413.576203] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[ 1413.576318] sd 9:0:0:0: Attached scsi generic sg6 type 0
```
Any one have any ideas on how to mount this photo viewer.  I currently have photos on it so I would know if I see files.  Thanks.

---

