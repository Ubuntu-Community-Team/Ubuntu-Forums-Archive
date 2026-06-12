---
title: "External Hardrive Problems"
date: 2009-12-04
forum: Hardware
---

### Post by FFGANDALF on 2009-12-04
My external hardrive is no longer being recongnized by Ubuntu the relevant dmesg output is


 1242.876132] usb 2-1: new high speed USB device using ehci_hcd and address 4
Dec  4 16:45:33 generic-laptop kernel: [ 1243.009897] usb 2-1: configuration #1 chosen from 1 choice
Dec  4 16:45:33 generic-laptop kernel: [ 1243.026265] scsi4 : SCSI emulation for USB Mass Storage devices
Dec  4 16:45:33 generic-laptop kernel: [ 1243.028978] input: Western Digital  My Book          as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/input/input14
Dec  4 16:45:33 generic-laptop kernel: [ 1243.029115] generic-usb 0003:1058:1101.0003: input,hidraw0: USB HID v1.10 Device [Western Digital  My Book         ] on usb-0000:00:1d.7-1/input1
Dec  4 16:45:38 generic-laptop kernel: [ 1248.025137] scsi 4:0:0:0: Direct-Access     WD                        1.65 PQ: 0 ANSI: 0
Dec  4 16:45:38 generic-laptop kernel: [ 1248.026508] sd 4:0:0:0: Attached scsi generic sg2 type 0
Dec  4 16:45:38 generic-laptop kernel: [ 1248.035178] sd 4:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Dec  4 16:45:38 generic-laptop kernel: [ 1248.036108] sd 4:0:0:0: [sdb] Using 0xffffffff as device size
Dec  4 16:45:38 generic-laptop kernel: [ 1248.036123] sd 4:0:0:0: [sdb] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
Dec  4 16:45:38 generic-laptop kernel: [ 1248.037706] sd 4:0:0:0: [sdb] Write Protect is off
Dec  4 16:45:38 generic-laptop kernel: [ 1248.038468] sd 4:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Dec  4 16:45:38 generic-laptop kernel: [ 1248.040078] sd 4:0:0:0: [sdb] Using 0xffffffff as device size
Dec  4 16:45:38 generic-laptop kernel: [ 1248.042232]  sdb:
Dec  4 16:45:38 generic-laptop kernel: [ 1248.043594] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  4 16:45:38 generic-laptop kernel: [ 1248.043604] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Dec  4 16:45:38 generic-laptop kernel: [ 1248.043615] Info fld=0x0
Dec  4 16:45:38 generic-laptop kernel: [ 1248.043620] sd 4:0:0:0: [sdb] Add. Sense: Logical block address out of range
Dec  4 16:45:38 generic-laptop kernel: [ 1248.043640] __ratelimit: 381 callbacks suppressed
Dec  4 16:45:38 generic-laptop kernel: [ 1248.048251] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  4 16:45:38 generic-laptop kernel: [ 1248.048261] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Dec  4 16:45:38 generic-laptop kernel: [ 1248.048272] Info fld=0x0
Dec  4 16:45:38 generic-laptop kernel: [ 1248.048276] sd 4:0:0:0: [sdb] Add. Sense: Logical block address out of range
Dec  4 16:45:38 generic-laptop kernel: [ 1248.049967] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  4 16:45:38 generic-laptop kernel: [ 1248.049976] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Dec  4 16:45:38 generic-laptop kernel: [ 1248.049987] Info fld=0x0

also in XP the drive doesn't show up but the icon on the taskbar with Western Digitals Logo that is for quick dismounting does show up.

---

### Post by JBAlaska on 2009-12-04
The kernel is trying to use a 16-byte read-capacity command, but it's failing. What is the capacity of this drive?

Just a wild guess. but it may have failed.

If you haven't already, install "smartmontools"
```
sudo apt-get install smartmontools
```

then run: ```
smartctl -a /dev/sdb

```

Please Post the output

---

### Post by FFGANDALF on 2009-12-06
It wouldn't run any tests, it said something to the effect that my hard drive didn't support smart tests.

---

### Post by FFGANDALF on 2009-12-06
> smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD        Version: 1.65
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

 I took its advice and got
> sudo smartctl -T verypermissive -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD        Version: 1.65
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
Device does not support Self Test logging


---

### Post by FFGANDALF on 2009-12-06
sorry about putting it in quotes I messed up on the formating.

---

