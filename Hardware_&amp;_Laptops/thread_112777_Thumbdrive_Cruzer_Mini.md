---
title: "Thumbdrive Cruzer Mini"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by raghav_p on 2006-01-05
My thumbdrive isn't working anymore.. not on Ubuntu nor on WinXP. dmesg says this:
```

[4294721.513000] hdc: command error: status=0x51 { DriveReady SeekComplete Error  }
[4294721.513000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294721.513000] ide: failed opcode was: unknown
[4294721.513000] end_request: I/O error, dev hdc, sector 8388520
[4294721.513000] Buffer I/O error on device hdc, logical block 2097130
[4294721.564000] hdc: command error: status=0x51 { DriveReady SeekComplete Error  }
[4294721.564000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294721.564000] ide: failed opcode was: unknown
[4294721.564000] end_request: I/O error, dev hdc, sector 8388524
[4294721.564000] Buffer I/O error on device hdc, logical block 2097131
[4294721.614000] hdc: command error: status=0x51 { DriveReady SeekComplete Error  }
[4294721.614000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294721.614000] ide: failed opcode was: unknown
[4294721.614000] end_request: I/O error, dev hdc, sector 8388520
[4294721.614000] Buffer I/O error on device hdc, logical block 2097130
[4294721.665000] hdc: command error: status=0x51 { DriveReady SeekComplete Error  }
[4294721.665000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense =0x05 }
[4294721.665000] ide: failed opcode was: unknown
[4294721.665000] end_request: I/O error, dev hdc, sector 8388524
[4294721.665000] Buffer I/O error on device hdc, logical block 2097131

```

I'm not sure if that means an error in just the partition or a complete disk failure. I don't have any critical data on the thumbdrive so a reformat is ok.

I guess my question is how do I reformat? Or.. is there anything I can do to save the drive?

---

### Post by mcduck on 2006-01-05
yep, most likely you can still save it. First, turn off autompunting of removable medias (in System/Preferences/removable drives and media if I remember right).Then plug the drive in and in terminal use 'fdisk hdc', delete the partition(s) from the disk and create a new FAT partition. save, exit, remove the drive, turn automounting on again and plug the drive back. It should work now. (you can use gparted or qparted to do the partitioning stuff with a graphical tool, both are available with apt-get/synaptic)

---

### Post by raghav_p on 2006-01-05
oh.. sorry..

it seems when I booted, I had a DVD in my drive -- hdc = dvd drive

the USB related dmesg's are as follows:

```

[4294766.005000] SCSI error : <0 0 0 0> return code = 0x70000
[4294766.005000] end_request: I/O error, dev sda, sector 0
[4294766.005000] Buffer I/O error on device sda, logical block 0
[4294766.006000] SCSI error : <0 0 0 0> return code = 0x70000
[4294766.006000] end_request: I/O error, dev sda, sector 0
[4294766.006000] Buffer I/O error on device sda, logical block 0
[4294766.006000]  unable to read partition table
[4294766.006000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294766.051000] sda : READ CAPACITY failed.
[4294766.051000] sda : status=0, message=00, host=7, driver=00
[4294766.051000] sda : sense not available.
[4294766.052000] sda: Write Protect is off
[4294766.052000] sda: Mode Sense: 00 00 00 00
[4294766.052000] sda: assuming drive cache: write through
[4294766.058000] sda : READ CAPACITY failed.
[4294766.058000] sda : status=0, message=00, host=7, driver=00
[4294766.058000] sda : sense not available.
[4294766.060000] sda: Write Protect is off
[4294766.060000] sda: Mode Sense: 00 00 00 00
[4294766.060000] sda: assuming drive cache: write through
[4294766.060000]  /dev/scsi/host0/bus0/target0/lun0:<3>Buffer I/O error on device sda, logical block 0
[4294766.060000] Buffer I/O error on device sda, logical block 0
[4294766.060000]  unable to read partition table
[4294766.061000] Buffer I/O error on device sda, logical block 0
[4294766.212000] usb 4-1: USB disconnect, address 2
[4294766.478000] scsi0 (0:0): rejecting I/O to dead device
[4294766.478000] scsi0 (0:0): rejecting I/O to dead device
[4294766.478000] scsi0 (0:0): rejecting I/O to dead device
[4294766.516000] scsi0 (0:0): rejecting I/O to dead device
[4294766.516000] scsi0 (0:0): rejecting I/O to dead device
[4294766.856000] scsi0 (0:0): rejecting I/O to dead device
[4294766.857000] scsi0 (0:0): rejecting I/O to dead device
[4294766.923000] scsi0 (0:0): rejecting I/O to dead device
[4294766.924000] scsi0 (0:0): rejecting I/O to dead device
[4294766.925000] scsi0 (0:0): rejecting I/O to dead device
[4294766.953000] scsi0 (0:0): rejecting I/O to dead device
[4294766.961000] scsi0 (0:0): rejecting I/O to dead device
[4294768.512000] scsi0 (0:0): rejecting I/O to dead device
[4294768.516000] scsi0 (0:0): rejecting I/O to dead device
[4294768.521000] scsi0 (0:0): rejecting I/O to dead device
[4294768.524000] scsi0 (0:0): rejecting I/O to dead device

```

NOTE: I unplugged USB drive when volume management was taking taking insane amount of time to load.

Then.. when I try fdisk sda, bash informs me that fdisk can't open sda.

---

### Post by mcduck on 2006-01-05
well, you could still try the same thing, only use sda instead of hdc ;)

oh, sorry, it's 'sudo fdisk /dev/sda'. If that doesn't work, try sdb, and sdc etc, as the device changes every time you plug/unplug it.

---

### Post by raghav_p on 2006-01-05
[QUOTE=mcduck]well, you could still try the same thing, only use sda instead of hdc ;)

oh, sorry, you might have to use 'sudo fdisk sda'[/QUOTE]

I tried that. Still can't open it. :(

gparted doesn't seem to work either

EDIT:

/dev/sda .. /dev/sdj don't work either

---

