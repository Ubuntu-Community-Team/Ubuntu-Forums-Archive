---
title: "Trouble mounting external HD; what's a sense key?"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by Halfling Rogue on 2007-09-27
I'm running Dapper on an IBM ThinkPad A20m. My external HD *will* usually mount after a couple of plugin/unplugs, but I'm pretty sure it's damaging to my drive to do that. The drive was named "LA HUEVOSA" on Windows, since I couldn't figure out how to rename it on Ubuntu, and during the drive's most recent mount I got an oops from gnome saying the drive couldn't be found and to check the spelling of the drive name--however, as soon as I clicked okay, the drive showed up anyway.

I'm mostly curious about the "sense key" returns I keep getting in /var/log/messages, which I think might be part of the problem. Here are a bunch of returns I got while plugging and unplugging the drive and tailing /messages. The very last one is the return for the time the drive actually mounted.

> Sep 27 16:33:32 localhost kernel: [ 1001.660644] usb 1-1: new full speed USB device using uhci_hcd and address 3
Sep 27 16:33:32 localhost kernel: [ 1001.805181] scsi1 : SCSI emulation for USB Mass Storage devices
Sep 27 16:33:37 localhost kernel: [ 1006.806769]   Vendor: WD        Model: 1600BEVExternal   Rev: 1.02
Sep 27 16:33:37 localhost kernel: [ 1006.806807]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 27 16:33:37 localhost kernel: [ 1006.811699] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 16:33:37 localhost kernel: [ 1006.816687] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 16:33:37 localhost kernel: [ 1006.816714]  sdb: sdb1
Sep 27 16:33:37 localhost kernel: [ 1006.865911] sd 1:0:0:0: Attached scsi disk sdb
Sep 27 16:33:37 localhost kernel: [ 1006.866028] sd 1:0:0:0: Attached scsi generic sg0 type 0
Sep 27 16:33:44 localhost kernel: [ 1013.342418] sdb: Current: sense key: No Sense
Sep 27 16:33:44 localhost kernel: [ 1013.342438]     Additional sense: No additional sense information
Sep 27 16:33:44 localhost kernel: [ 1013.342456] Info fld=0x0
Sep 27 16:33:47 localhost kernel: [ 1016.451388] sdb: Current: sense key: No Sense
Sep 27 16:33:47 localhost kernel: [ 1016.451408]     Additional sense: No additional sense information
Sep 27 16:33:47 localhost kernel: [ 1016.451426] Info fld=0x0
Sep 27 16:33:54 localhost kernel: [ 1023.831556] sdb: Current: sense key: No Sense
Sep 27 16:33:54 localhost kernel: [ 1023.831575]     Additional sense: No additional sense information
Sep 27 16:33:54 localhost kernel: [ 1023.831593] Info fld=0x0

*

Sep 27 16:40:37 localhost kernel: [ 1436.417820] usb 1-1: USB disconnect, address 7
Sep 27 16:40:50 localhost kernel: [ 1446.549445] usb 1-1: new full speed USB device using uhci_hcd and address 8
Sep 27 16:40:50 localhost kernel: [ 1446.693752] scsi6 : SCSI emulation for USB Mass Storage devices
Sep 27 16:40:53 localhost kernel: [ 1140.878171]   Vendor: WD        Model: 1600BEVExternal   Rev: 1.02
Sep 27 16:40:53 localhost kernel: [ 1140.878207]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 27 16:40:53 localhost kernel: [ 1140.884108] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 16:40:53 localhost kernel: [ 1140.890362] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 16:40:53 localhost kernel: [ 1140.890385]  sdb: sdb1
Sep 27 16:40:53 localhost kernel: [ 1140.947254] sd 6:0:0:0: Attached scsi disk sdb
Sep 27 16:40:53 localhost kernel: [ 1140.947351] sd 6:0:0:0: Attached scsi generic sg0 type 0
Sep 27 16:40:56 localhost kernel: [ 1456.245425] sdb: Current: sense key: No Sense
Sep 27 16:40:56 localhost kernel: [ 1456.245445]     Additional sense: No additional sense information
Sep 27 16:40:56 localhost kernel: [ 1456.245463] Info fld=0x0
Sep 27 16:41:00 localhost kernel: [ 1460.133534] sdb: Current: sense key: No Sense
Sep 27 16:41:00 localhost kernel: [ 1460.133555]     Additional sense: No additional sense information
Sep 27 16:41:00 localhost kernel: [ 1460.133573] Info fld=0x0
Sep 27 16:41:09 localhost kernel: [ 1153.734407] sdb: Current: sense key: No Sense
Sep 27 16:41:09 localhost kernel: [ 1153.734425]     Additional sense: No additional sense information
Sep 27 16:41:09 localhost kernel: [ 1153.734440] Info fld=0x0
Sep 27 16:41:24 localhost kernel: [ 1487.528771] sd 6:0:0:0: SCSI error: return code = 0x8000002
Sep 27 16:41:24 localhost kernel: [ 1487.528790] sdb: Current: sense key: Medium Error
Sep 27 16:41:24 localhost kernel: [ 1487.528799]     Additional sense: Id CRC or ECC error
Sep 27 16:41:24 localhost kernel: [ 1487.528817] Info fld=0x0
Sep 27 16:41:24 localhost kernel: [ 1487.528824] end_request: I/O error, dev sdb, sector 63
Sep 27 16:41:27 localhost kernel: [ 1171.038539] sdb: Current: sense key: No Sense
Sep 27 16:41:27 localhost kernel: [ 1171.038557]     Additional sense: No additional sense information
Sep 27 16:41:27 localhost kernel: [ 1171.038572] Info fld=0x0
Sep 27 16:42:27 localhost kernel: [ 1229.317413] usb 1-1: USB disconnect, address 8

*

Sep 27 17:05:22 localhost kernel: [ 2974.369624] usb 1-1: USB disconnect, address 16
Sep 27 17:05:31 localhost kernel: [ 2983.733556] usb 1-1: new full speed USB device using uhci_hcd and address 17
Sep 27 17:05:31 localhost kernel: [ 2983.878104] scsi15 : SCSI emulation for USB Mass Storage devices
Sep 27 17:05:36 localhost kernel: [ 2988.879669]   Vendor: WD        Model: 1600BEVExternal   Rev: 1.02
Sep 27 17:05:36 localhost kernel: [ 2988.879707]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 27 17:05:36 localhost kernel: [ 2988.885619] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 17:05:36 localhost kernel: [ 2988.891598] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 17:05:36 localhost kernel: [ 2988.891626]  sdb: sdb1
Sep 27 17:05:36 localhost kernel: [ 2988.944253] sd 15:0:0:0: Attached scsi disk sdb
Sep 27 17:05:36 localhost kernel: [ 2988.944366] sd 15:0:0:0: Attached scsi generic sg0 type 0
Sep 27 17:05:43 localhost kernel: [ 2995.571221] sdb: Current: sense key: No Sense
Sep 27 17:05:43 localhost kernel: [ 2995.571241]     Additional sense: No additional sense information
Sep 27 17:05:43 localhost kernel: [ 2995.571259] Info fld=0x0
Sep 27 17:05:46 localhost kernel: [ 2998.872067] sdb: Current: sense key: No Sense
Sep 27 17:05:46 localhost kernel: [ 2998.872088]     Additional sense: No additional sense information
Sep 27 17:05:46 localhost kernel: [ 2998.872106] Info fld=0x0
Sep 27 17:05:54 localhost kernel: [ 3006.939630] usb 1-1: USB disconnect, address 17
Sep 27 17:05:56 localhost kernel: [ 3006.943642]  15:0:0:0: SCSI error: return code = 0x10000
Sep 27 17:05:56 localhost kernel: [ 3006.943657] end_request: I/O error, dev sdb, sector 64
Sep 27 17:05:57 localhost kernel: [ 3006.943878]  15:0:0:0: SCSI error: return code = 0x10000
Sep 27 17:05:57 localhost kernel: [ 3006.943887] end_request: I/O error, dev sdb, sector 76399

*

Sep 27 17:06:20 localhost kernel: [ 3032.600539] usb 1-1: new full speed USB device using uhci_hcd and address 18
Sep 27 17:06:20 localhost kernel: [ 3032.745054] scsi16 : SCSI emulation for USB Mass Storage devices
Sep 27 17:06:25 localhost kernel: [ 2386.648718]   Vendor: WD        Model: 1600BEVExternal   Rev: 1.02
Sep 27 17:06:25 localhost kernel: [ 2386.648750]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 27 17:06:25 localhost kernel: [ 2386.653652] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 17:06:25 localhost kernel: [ 2386.658660] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Sep 27 17:06:25 localhost kernel: [ 2386.658687]  sdb: sdb1
Sep 27 17:06:25 localhost kernel: [ 2386.712834] sd 16:0:0:0: Attached scsi disk sdb
Sep 27 17:06:25 localhost kernel: [ 2386.712948] sd 16:0:0:0: Attached scsi generic sg0 type 0
Sep 27 17:06:32 localhost kernel: [ 3046.083314] sdb: Current: sense key: No Sense
Sep 27 17:06:32 localhost kernel: [ 3046.083335]     Additional sense: No additional sense information
Sep 27 17:06:32 localhost kernel: [ 3046.083352] Info fld=0x0
Sep 27 17:06:38 localhost kernel: [ 3052.305235] sdb: Current: sense key: No Sense
Sep 27 17:06:38 localhost kernel: [ 3052.305255]     Additional sense: No additional sense information
Sep 27 17:06:38 localhost kernel: [ 3052.305273] Info fld=0x0
Sep 27 17:06:42 localhost kernel: [ 3056.043789] sdb: Current: sense key: No Sense
Sep 27 17:06:42 localhost kernel: [ 3056.043808]     Additional sense: No additional sense information
Sep 27 17:06:42 localhost kernel: [ 3056.043826] Info fld=0x0
Sep 27 17:06:46 localhost kernel: [ 3059.488535] sdb: Current: sense key: No Sense
Sep 27 17:06:46 localhost kernel: [ 3059.488556]     Additional sense: No additional sense information
Sep 27 17:06:46 localhost kernel: [ 3059.488574] Info fld=0x0


---

### Post by Halfling Rogue on 2007-10-09
So according to [this]("http://ubuntuforums.org/showpost.php?p=2421970&postcount=5"), the sense key is apparently not the problem, so I'm completely stumped.

It couldn't be the kernel, could it?

---

### Post by CaptainInsaneO on 2007-10-27
You should never unplug/turn off your external hdd's without unmounting them first.

To do this easily through a GUI, to go Places>Computer and then right click your external drive, and then select "Unmount Volume". I have two externals myself and if I forget to do this, I can't remount the drive under Ubuntu unless I reboot into Windows and shut it down cleanly or I use ntfsfix.

Every time I unmount my volumes first, however, I can then flip the switch on the drive, and then 5 seconds later I can turn it back on without fail.

---

### Post by Halfling Rogue on 2007-10-27
I don't unplug it without unmounting now, but even if I unmount it first before unplugging it (it doesn't have a switch), Ubuntu still won't remount it without a reboot.

---

### Post by CaptainInsaneO on 2007-10-27
Have you tried manually mounting it through the terminal?

---

### Post by Halfling Rogue on 2007-11-26
It can't mount it if it can't even tell anything is there, can it?

---

