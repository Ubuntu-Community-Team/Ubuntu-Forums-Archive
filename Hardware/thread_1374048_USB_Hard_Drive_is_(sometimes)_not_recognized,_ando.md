---
title: "USB Hard Drive is (sometimes) not recognized, and/or suddenly unmounts while working"
date: 2010-01-06
forum: Hardware
---

### Post by Nonninz on 2010-01-06
Hello everybody.

After upgrading to Karmic my laptop begun having a strange behaviour regarding my external hard drive, a LACIE 500GB disk.

At what seems random times, the hard drive partitions are not automagically mounted by GNOME anymore, and there is no way to mount them manually.
If the drive is already plugged in since boot time, partitions may be already mounted when gnome starts OR be mounted some time later, with the nautilus windows popping up on the screen showing the disk contents.
The same thing when it is hot-plugged: sometimes the partitions are detected immediately, sometimes it takes a while, and sometimes the drive is ignored.
Additionally, even when it's working ok there is a chance that it will suddenly cease functioning, apps cannot write/read files to it anymore causing serious errors (the drive also holds some virtualbox machines' virtual drives).

This is happening on my laptop, a COMPAL HEL80/81 with karmic, and it didn't happen before the upgrade.

I include some output, after that the hard disk has abruptly ceased "functioning", and after i tried unplugging and plugging it back a couple times:

uname - a:
```
Linux caspar 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
```

lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 004 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 011: ID 059f:1021 LaCie, Ltd **
Bus 001 Device 007: ID 10fd:0535 Anubis Electronics, Ltd 
Bus 001 Device 004: ID 0c45:624f Microdia PC Camera (SN9C201 + OV9650)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

fdisk -l:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006a764

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229        5246      144585   83  Linux
/dev/sda3            5247       12161    55544737+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097383

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       52268   419842678+   7  HPFS/NTFS
/dev/sdc2           52269       54920    21302190   83  Linux
/dev/sdc3           54921       60801    47239132+  83  Linux
```

As you can see, the hard drive is indeed recognized as sdc. **But**:

ls -l /dev/sd*:
```
brw-rw---- 1 root disk 8,  0 2010-01-06 12:11 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-01-06 12:11 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-01-06 12:11 /dev/sda2
brw-rw---- 1 root disk 8,  3 2010-01-06 12:11 /dev/sda3
brw-rw---- 1 root disk 8, 32 2010-01-06 16:23 /dev/sdc
```

The node files under /dev are not there!

This is an (extended) output of dmesg after the first trial of un/replug:

```
[13440.604439] INFO: task sync:11944 blocked for more than 120 seconds.
[13440.604444] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[13440.604448] sync          D c08145c0     0 11944  11941 0x00000000
[13440.604455]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[13440.604464]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[13440.604473]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[13440.604481] Call Trace:
[13440.604492]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[13440.604497]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[13440.604508]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[13440.604513]  [<c05701b7>] ? down_read+0x17/0x20
[13440.604518]  [<c0207875>] sync_filesystems+0xb5/0x100
[13440.604522]  [<c0207901>] sys_sync+0x11/0x40
[13440.604527]  [<c010336c>] syscall_call+0x7/0xb
[13560.605075] INFO: task sync:11944 blocked for more than 120 seconds.
[13560.605080] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[13560.605083] sync          D c08145c0     0 11944  11941 0x00000000
[13560.605089]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[13560.605097]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[13560.605104]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[13560.605111] Call Trace:
[13560.605121]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[13560.605125]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[13560.605129]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[13560.605133]  [<c05701b7>] ? down_read+0x17/0x20
[13560.605138]  [<c0207875>] sync_filesystems+0xb5/0x100
[13560.605141]  [<c0207901>] sys_sync+0x11/0x40
[13560.605146]  [<c010336c>] syscall_call+0x7/0xb
[13680.605096] INFO: task sync:11944 blocked for more than 120 seconds.
[13680.605101] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[13680.605105] sync          D c08145c0     0 11944  11941 0x00000000
[13680.605110]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[13680.605118]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[13680.605125]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[13680.605133] Call Trace:
[13680.605143]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[13680.605147]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[13680.605151]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[13680.605156]  [<c05701b7>] ? down_read+0x17/0x20
[13680.605161]  [<c0207875>] sync_filesystems+0xb5/0x100
[13680.605164]  [<c0207901>] sys_sync+0x11/0x40
[13680.605169]  [<c010336c>] syscall_call+0x7/0xb
[13800.605069] INFO: task sync:11944 blocked for more than 120 seconds.
[13800.605074] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[13800.605077] sync          D c08145c0     0 11944  11941 0x00000000
[13800.605082]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[13800.605090]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[13800.605098]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[13800.605105] Call Trace:
[13800.605115]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[13800.605124]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[13800.605128]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[13800.605132]  [<c05701b7>] ? down_read+0x17/0x20
[13800.605136]  [<c0207875>] sync_filesystems+0xb5/0x100
[13800.605140]  [<c0207901>] sys_sync+0x11/0x40
[13800.605144]  [<c010336c>] syscall_call+0x7/0xb
[13920.605101] INFO: task sync:11944 blocked for more than 120 seconds.
[13920.605110] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[13920.605116] sync          D c08145c0     0 11944  11941 0x00000000
[13920.605127]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[13920.605142]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[13920.605156]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[13920.605171] Call Trace:
[13920.605186]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[13920.605194]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[13920.605202]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[13920.605210]  [<c05701b7>] ? down_read+0x17/0x20
[13920.605219]  [<c0207875>] sync_filesystems+0xb5/0x100
[13920.605226]  [<c0207901>] sys_sync+0x11/0x40
[13920.605233]  [<c010336c>] syscall_call+0x7/0xb
[14040.605072] INFO: task sync:11944 blocked for more than 120 seconds.
[14040.605077] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[14040.605080] sync          D c08145c0     0 11944  11941 0x00000000
[14040.605086]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[14040.605094]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[14040.605101]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[14040.605109] Call Trace:
[14040.605119]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[14040.605123]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[14040.605127]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[14040.605131]  [<c05701b7>] ? down_read+0x17/0x20
[14040.605136]  [<c0207875>] sync_filesystems+0xb5/0x100
[14040.605140]  [<c0207901>] sys_sync+0x11/0x40
[14040.605144]  [<c010336c>] syscall_call+0x7/0xb
[14160.605112] INFO: task sync:11944 blocked for more than 120 seconds.
[14160.605120] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[14160.605127] sync          D c08145c0     0 11944  11941 0x00000000
[14160.605137]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[14160.605152]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[14160.605167]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[14160.605181] Call Trace:
[14160.605197]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[14160.605205]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[14160.605213]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[14160.605221]  [<c05701b7>] ? down_read+0x17/0x20
[14160.605229]  [<c0207875>] sync_filesystems+0xb5/0x100
[14160.605236]  [<c0207901>] sys_sync+0x11/0x40
[14160.605244]  [<c010336c>] syscall_call+0x7/0xb
[14280.605118] INFO: task sync:11944 blocked for more than 120 seconds.
[14280.605126] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[14280.605132] sync          D c08145c0     0 11944  11941 0x00000000
[14280.605142]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[14280.605158]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[14280.605172]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[14280.605186] Call Trace:
[14280.605201]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[14280.605209]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[14280.605217]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[14280.605225]  [<c05701b7>] ? down_read+0x17/0x20
[14280.605234]  [<c0207875>] sync_filesystems+0xb5/0x100
[14280.605241]  [<c0207901>] sys_sync+0x11/0x40
[14280.605248]  [<c010336c>] syscall_call+0x7/0xb
[14400.605149] INFO: task sync:11944 blocked for more than 120 seconds.
[14400.605157] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[14400.605164] sync          D c08145c0     0 11944  11941 0x00000000
[14400.605174]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[14400.605189]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[14400.605203]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[14400.605218] Call Trace:
[14400.605233]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[14400.605241]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[14400.605249]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[14400.605257]  [<c05701b7>] ? down_read+0x17/0x20
[14400.605265]  [<c0207875>] sync_filesystems+0xb5/0x100
[14400.605272]  [<c0207901>] sys_sync+0x11/0x40
[14400.605280]  [<c010336c>] syscall_call+0x7/0xb
[14520.605125] INFO: task sync:11944 blocked for more than 120 seconds.
[14520.605133] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[14520.605139] sync          D c08145c0     0 11944  11941 0x00000000
[14520.605149]  e7bc9f2c 00000082 00000000 c08145c0 e8784168 c08145c0 7efa22b5 00000c06
[14520.605165]  c08145c0 c08145c0 e8784168 c08145c0 7ef9be15 00000c06 c08145c0 f50be540
[14520.605179]  e8783ed0 e7bc9f60 e8783ed0 f1a2883c e7bc9f58 c0570a25 fffeffff f57bf200
[14520.605193] Call Trace:
[14520.605208]  [<c0570a25>] rwsem_down_failed_common+0x75/0x1a0
[14520.605217]  [<c0570b9d>] rwsem_down_read_failed+0x1d/0x30
[14520.605225]  [<c0570bf7>] call_rwsem_down_read_failed+0x7/0x10
[14520.605233]  [<c05701b7>] ? down_read+0x17/0x20
[14520.605241]  [<c0207875>] sync_filesystems+0xb5/0x100
[14520.605248]  [<c0207901>] sys_sync+0x11/0x40
[14520.605256]  [<c010336c>] syscall_call+0x7/0xb
[14748.725297] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[14768.459814] usb 1-1: USB disconnect, address 10
[14769.808146] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[14769.808157] usb 4-1: USB disconnect, address 4
[14770.072061] usb 4-1: new low speed USB device using uhci_hcd and address 5
[14770.271541] usb 4-1: configuration #1 chosen from 1 choice
[14770.324055] input: HID 1241:1166 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input10
[14770.324166] generic-usb 0003:1241:1166.0003: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.2-1/input0
[14774.600268] usb 1-1: new high speed USB device using ehci_hcd and address 11
[14774.733506] usb 1-1: configuration #1 chosen from 1 choice
[14774.735209] scsi5 : SCSI emulation for USB Mass Storage devices
[14774.735530] usb-storage: device found at 11
[14774.735535] usb-storage: waiting for device to settle before scanning
[14779.732347] usb-storage: device scan complete
[14779.732975] scsi 5:0:0:0: Direct-Access     SAMSUNG  HM500LI               PQ: 0 ANSI: 2 CCS
[14779.734658] sd 5:0:0:0: Attached scsi generic sg2 type 0
[14779.736627] sd 5:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[14779.737618] sd 5:0:0:0: [sdc] Write Protect is off
[14779.737626] sd 5:0:0:0: [sdc] Mode Sense: 34 00 00 00
[14779.737631] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[14779.739109] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[14779.739117]  sdc: sdc1 sdc2 sdc3
[14779.774362] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[14779.774369] sd 5:0:0:0: [sdc] Attached SCSI disk
```

This goes back in time, as i don't know haow many of that are related to the hard drive...

Finally, just the dmesg output that occurs after unplugging and plugging the drive back:
```
[15150.033868] usb 1-1: USB disconnect, address 11
[15158.128068] usb 1-1: new high speed USB device using ehci_hcd and address 12
[15158.261649] usb 1-1: configuration #1 chosen from 1 choice
[15158.265491] scsi6 : SCSI emulation for USB Mass Storage devices
[15158.265944] usb-storage: device found at 12
[15158.265949] usb-storage: waiting for device to settle before scanning
[15163.265270] usb-storage: device scan complete
[15163.265893] scsi 6:0:0:0: Direct-Access     SAMSUNG  HM500LI               PQ: 0 ANSI: 2 CCS
[15163.266803] sd 6:0:0:0: Attached scsi generic sg2 type 0
[15163.272185] sd 6:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[15163.273044] sd 6:0:0:0: [sdc] Write Protect is off
[15163.273047] sd 6:0:0:0: [sdc] Mode Sense: 34 00 00 00
[15163.273050] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[15163.274771] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[15163.274776]  sdc: sdc1 sdc2 sdc3
[15163.306540] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[15163.306546] sd 6:0:0:0: [sdc] Attached SCSI disk

```

Any help would be GREATLY appreciated. Thank you very much!

---

### Post by Nonninz on 2010-01-06
A brief update.

Checking syslog, the last lines (trimmed by some gibberish from wpa_supplicant) contain:

```
Jan  6 16:23:46 caspar kernel: [15163.274776]  sdc: sdc1 sdc2 sdc3
Jan  6 16:23:46 caspar kernel: [15163.306540] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Jan  6 16:23:46 caspar kernel: [15163.306546] sd 6:0:0:0: [sdc] Attached SCSI disk
Jan  6 16:24:17 caspar wpa_supplicant[1509]: CTRL-EVENT-SCAN-RESULTS 
Jan  6 16:26:17 caspar wpa_supplicant[1509]: CTRL-EVENT-SCAN-RESULTS 
Jan  6 16:26:46 caspar udevd[648]: worker [13273] unexpectedly returned with status 0x0100
Jan  6 16:26:46 caspar udevd[648]: worker [13273] failed while handling '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:0/block/sdc'
```

So, it looks like udev fails handling the disk... is this a base for sending a bug report to udev or am I wrong?

Thanks again

---

### Post by Nonninz on 2010-01-06
Another update (do you prefer me insted to edit previous posts?).

I shut off the laptop, but it froze while displaying the message:

* Shutting down ALSA system...

So I had to turn it off the hard way.

I tried rebooting the pc with the hd still plugged in, but the drive partitions weren't mounted (but they appeared in the "Places" menu).

After i click on one of these, I waited a while until a popup appeared saying that the partition couldn't be mounted. Soon after i closed the popup, I heard some activity coming from the drive and after a couple seconds all three partitions got mounted and displayed on screen.

This is the output of syslog after this last operation:

```
Jan  6 17:17:58 caspar kernel: [  599.056482] sd 2:0:0:0: Device offlined - not ready after error recovery
Jan  6 17:17:58 caspar kernel: [  599.056494] sd 2:0:0:0: [sdb] Unhandled error code
Jan  6 17:17:58 caspar kernel: [  599.056497] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan  6 17:17:58 caspar kernel: [  599.056501] end_request: I/O error, dev sdb, sector 882289800
Jan  6 17:17:58 caspar kernel: [  599.056526] XFS: SB read failed
Jan  6 17:17:58 caspar kernel: [  599.056826] usb 1-1: USB disconnect, address 2
Jan  6 17:17:58 caspar kernel: [  599.332065] usb 1-1: new high speed USB device using ehci_hcd and address 8
Jan  6 17:17:58 caspar kernel: [  599.473533] usb 1-1: configuration #1 chosen from 1 choice
Jan  6 17:17:58 caspar kernel: [  599.485160] scsi3 : SCSI emulation for USB Mass Storage devices
Jan  6 17:17:58 caspar kernel: [  599.487820] usb-storage: device found at 8
Jan  6 17:17:58 caspar kernel: [  599.487826] usb-storage: waiting for device to settle before scanning
Jan  6 17:18:03 caspar kernel: [  604.488281] usb-storage: device scan complete
Jan  6 17:18:03 caspar kernel: [  604.530494] scsi 3:0:0:0: Direct-Access     SAMSUNG  HM500LI               PQ: 0 ANSI: 2 CCS
Jan  6 17:18:03 caspar kernel: [  604.531067] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jan  6 17:18:04 caspar kernel: [  604.604785] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jan  6 17:18:04 caspar kernel: [  604.605733] sd 3:0:0:0: [sdb] Write Protect is off
Jan  6 17:18:04 caspar kernel: [  604.605742] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
Jan  6 17:18:04 caspar kernel: [  604.605748] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan  6 17:18:04 caspar kernel: [  604.607587] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan  6 17:18:04 caspar kernel: [  604.607599]  sdb: sdb1 sdb2 sdb3
Jan  6 17:18:04 caspar kernel: [  604.635908] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan  6 17:18:04 caspar kernel: [  604.635917] sd 3:0:0:0: [sdb] Attached SCSI disk
Jan  6 17:18:04 caspar kernel: [  605.397038] XFS mounting filesystem sdb2
Jan  6 17:18:04 caspar kernel: [  605.507905] XFS mounting filesystem sdb3
Jan  6 17:18:06 caspar ntfs-3g[3110]: Version 2009.4.4 external FUSE 27
Jan  6 17:18:06 caspar ntfs-3g[3110]: Mounted /dev/sdb1 (Read-Write, label "Storage", NTFS 3.1)
Jan  6 17:18:06 caspar ntfs-3g[3110]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Jan  6 17:18:06 caspar ntfs-3g[3110]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Jan  6 17:18:07 caspar kernel: [  607.956438] Ending clean XFS mount for filesystem: sdb3
Jan  6 17:18:07 caspar kernel: [  608.038924] Ending clean XFS mount for filesystem: sdb2
Jan  6 17:19:14 caspar wpa_supplicant[1524]: CTRL-EVENT-SCAN-RESULTS 

```

---

### Post by checksquid on 2010-01-09
Just a shot in the dark--I'm a newbie with a similar problem. You might want to look at this thread, just in case it's related:
[http://ubuntuforums.org/showthread.php?t=1333205&highlight=ntfs+external+mount]("http://ubuntuforums.org/showthread.php?t=1333205&highlight=ntfs+external+mount")
It concerns a problem mounting NTFS partitions on external drives.

---

### Post by Nonninz on 2010-01-10
Thank you very much for your help. Unfortunately that thread deals with a different problem... :(

Another information:
If my hard disk is in use while I switch from battery to ac power (and the opposite), the hard drive stops working for a while, its led turn off, and after like 10 second it wakes up again.
For now it happened only once, and the system didn't unmount the partitions during the short "turned off time". I'll see if it happens another time.

---

### Post by sym_zo on 2010-02-11
It seems I have the same problem you have, Nonninz. I haven't found a solution either :-(.

Is there somebody out there to help us ?

---

### Post by sym_zo on 2010-02-12
Ok, I found an alternative to rebooting. It's ugly, but it works : 

[LIST=1]
[*] Unplug the drive
[*] (might not be necessary) Run partprobe to clear any trace of the device : ```
sudo partprobe
``` Note : partprobe seems to wait for a 180sec before ending (a timeout setting of udev). You have to be patient :P.
[*] Plug the device back in.
[*] Run partprobe again. The drive and it's partitions should now appear in /dev.```
sudo partprobe
```
[*] Trigger automount, where /dev/sdc1 is the partition you want to mount. Be careful not to use sudo here, otherwise the drive will not be readable for a normal user.```
devkit-disks --mount /dev/sdc1
```
[/LIST] 



It's far from perfect and I'm sure a more knowledgeable user could come up with a better procedure, but at least I don't have to reboot anymore :).

---

### Post by root52 on 2010-02-27
Hi All,

Just thought I would add to this some infromation about my setup as I have been struggling with this for a bit now.  

Ubuntu 9.10

Linux none 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

dmesg...

> [13830.895114] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[13830.895128] usb 4-1: USB disconnect, address 4
[13830.896083] ohci_hcd 0000:00:06.0: dev 1 ep1in scatterlist error -108/-108
[13830.896266] sd 7:0:0:0: [sdb] Unhandled error code
[13830.896273] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[13830.896282] end_request: I/O error, dev sdb, sector 543345607
[13830.896431] sd 7:0:0:0: [sdb] Unhandled error code
[13830.896437] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[13830.896445] end_request: I/O error, dev sdb, sector 543345847
[13830.898587] JBD2: Detected IO errors while flushing file data on sdb1:8
[13830.899541] Aborting journal on device sdb1:8.
[13830.899619] JBD2: I/O error detected when updating journal superblock for sdb1:8.
[13830.899675] EXT4-fs error (device sdb1) in ext4_reserve_inode_write: Journal has aborted
[13830.899711] journal commit I/O error
[13830.899730] EXT4-fs error (device sdb1) in ext4_dirty_inode: Journal has aborted
[13830.899739] EXT4-fs (sdb1): previous I/O error to superblock detected
[13830.899778] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal
[13830.899793] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal


The device is a Seagate FreeAgent 500gb USB 2.0 drive. I seem to have the same problem where it will after an amount of time just "reset" the usb port causing it to unmount unclean and data to be damaged. For me a reboot and a power cycle of the drive is the only fix I know of. 

If anybody has some insight as to what is going on (our some suggestions on other places to look for a clue as to the root cause) that would be super. 

Thanks!!

---

### Post by root52 on 2010-02-27
Sorry, forgot to mention I have a asus ion at3n7a-i main board. The drive is formatted EXT4...

---

### Post by savaan on 2010-04-18
I'm having the exact same issue with a Seagate USB external 250gig. Drive unmounts itself and damages data. Now theres data on there that won't allow me to delete.

---

### Post by jalefkowit on 2010-06-25
I am having this issue too.  I used to have a 250GB Western Digital My Book external drive (connected via USB2) and I recently replaced it with a Hitachi 1TB desktop hard drive in a Rosewill enclosure (also via USB2).  The new setup unmounts less frequently than the old one did but it does still happen annoyingly often.

---

### Post by Darvinia on 2010-08-13
I've been fighting this problem for almost a week with a Seagate 160 gb usb external drive.  Haven't found anything on the net that has worked for me.  This thread is the one that best describes my problem so was hoping to find a fix here.  At least this post will bump it up and maybe get some more attention.

---

### Post by savaan on 2010-08-14
Tried a few things including reformatting the drive for Linux as opposed to FAT32 but I still get the same problems. I can't play movies or music off the drive because the drive will auto-dismount after a short time. Or at least I 'believe' that it dismounts. It no longer shows up in my "Places" menu. The only thing I can do to get it back is to unplug it and plug it back in

---

### Post by bumder on 2010-09-03
ditto

[http://ubuntuforums.org/showthread.php?t=1564089](http://ubuntuforums.org/showthread.php?t=1564089)

IOMEGA PRESTIGE 1TB
Samsung NC10
10.04 LTS

---

### Post by genobee on 2010-09-16
Hi,

 I have this same problem too after doing a fresh install of Lucid Lynx. My hard drive is a WD 250GB.

 I just would like to add that this problem has not yet occurred when I mount my cell phone as a USB mass storage.

Thank you,

---

### Post by savaan on 2010-09-16
I've noticed that my digital camera doesn't time out either. It's just the hard drive. Someone said that it might be the hard drives 'time out' feature in the software, but I've yet to find it :( Now...the hard drive in question also says that it has a few bad sectors. Could these be the cause? Or could the frequent dismounts have lead to bad sectors?

---

### Post by Budoc on 2010-09-23
Hi,

I've had random disconnections for several drives, both USB-powered and externally powered, and for several different formats. I believe that my problem is this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349767") which has been reported on launchpad. Perhaps your problems are related too?

---

### Post by ZhuaSD on 2010-09-24
Thanks for the link Budoc, that looks like just the problem I have been having with a WD 250 g drive, for years now.

Hopefully now that it is identified it can be fixed.

---

### Post by oblivious on 2010-10-24
I am having the same problem, my external HDD (IOMEGA 1.5TB) unmounts itself. In my case I realized it was happening because I leave my torrents downloading overnight. Since installing Lucid Linx, sometimes when I check my download progress in the morning (Transmission) the torrents are all reporting an I/O error. I check the hard drive in Nautilus and its not there.

For me, a simple power cycle in the external HDD is enough to restore the situation. The drive is always recognized and mounted correctly.

Reading the responses here and the related links, the problem seems to be related to intensive I/O (downloading, watching long movies).

Maybe this could point more knowledgeable users in the right direction to help us here.

---

