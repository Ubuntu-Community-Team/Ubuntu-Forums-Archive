---
title: "Dvd/cd drive not working"
date: 2010-03-30
forum: Hardware
---

### Post by Lrpbpb on 2010-03-30
I know this has been posted many times... but my dvd/cd drive is not working, it doesn't detect any media, any cd insert be it movie dvd, music or data isn't detected in anyway. 

I have read around the forums to try to solve this but the only answers I have gotten is change the AHCI mode to IDE, which I have no idea how to do....I think this can be done in the BIOS but I can't find how and also the bios does detect it. Another solution was changing kernels, but I have tried and have used both the latest and the one that came with ubuntu- nothing. I have also found that it may be something with grub, but I have no idea how to change it to another bootloader, or am afraid to do so and screw it up and having to (once again) reinstall ubuntu and xp.

I would want to know how to correct this problem, as the drive works perfectly in windows (drivers perhaps?), and any help would be greatly appreciated.:)

*Edit: I also ran "sudo lshw -c disk" and my drive was shown, but still no media I insert works

**Edit: I inserted an audio cd and it was recognized, but still nothing from dvd's and other cd's

---

### Post by anglican on 2010-04-01
> **Lrpbpb said:**
> I know this has been posted many times... but my dvd/cd drive is not working, it doesn't detect any media, any cd insert be it movie dvd, music or data isn't detected in anyway. 

I have read around the forums to try to solve this but the only answers I have gotten is change the AHCI mode to IDE, which I have no idea how to do....I think this can be done in the BIOS but I can't find how and also the bios does detect it. Another solution was changing kernels, but I have tried and have used both the latest and the one that came with ubuntu- nothing. I have also found that it may be something with grub, but I have no idea how to change it to another bootloader, or am afraid to do so and screw it up and having to (once again) reinstall ubuntu and xp.

I would want to know how to correct this problem, as the drive works perfectly in windows (drivers perhaps?), and any help would be greatly appreciated.:)

*Edit: I also ran "sudo lshw -c disk" and my drive was shown, but still no media I insert works

You're not giving enough information here to stand any chance of getting an answer. As a minimum, you need to show that last ~20 lines of the output from the command "dmesg" **after** you've inserted a disk. Depending on what that shows there may be other pertinent information to provide...

H

---

### Post by Lrpbpb on 2010-04-01
This is what I get after inserting a dvd:
 
```
[ 9593.621791] FAT: bread failed in fat_clusters_flush
[ 9596.672162] __ratelimit: 29 callbacks suppressed
[ 9596.672166] nautilus[9420]: segfault at 8bffffeb ip 0020c803 sp bfd5fd80 error 4 in libgobject-2.0.so.0.2200.3[1e7000+3c000]
[ 9603.133313] usb 1-5: USB disconnect, address 7
[ 9603.264039] usb 1-6: USB disconnect, address 6
[ 9603.508722] usb 1-6: new high speed USB device using ehci_hcd and address 8
[ 9603.642385] usb 1-6: configuration #1 chosen from 1 choice
[ 9603.650224] scsi7 : SCSI emulation for USB Mass Storage devices
[ 9603.650375] usb-storage: device found at 8
[ 9603.650377] usb-storage: waiting for device to settle before scanning
[ 9604.828025] usb 1-5: new high speed USB device using ehci_hcd and address 9
[ 9604.969007] usb 1-5: configuration #1 chosen from 1 choice
[ 9604.970864] scsi8 : SCSI emulation for USB Mass Storage devices
[ 9604.971047] usb-storage: device found at 9
[ 9604.971049] usb-storage: waiting for device to settle before scanning
[ 9608.648214] usb-storage: device scan complete
[ 9608.648945] scsi 7:0:0:0: Direct-Access     Corsair  Voyager Mini     0.00 PQ: 0 ANSI: 2
[ 9608.649509] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 9608.650170] sd 7:0:0:0: [sdb] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[ 9608.650790] sd 7:0:0:0: [sdb] Write Protect is off
[ 9608.650794] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 9608.650797] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9608.656165] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9608.656171]  sdb: sdb1
[ 9608.800915] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9608.800920] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 9609.968959] usb-storage: device scan complete
[ 9609.969444] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[ 9609.969876] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 9609.976190] sd 8:0:0:0: [sdc] 3940351 512-byte logical blocks: (2.01 GB/1.87 GiB)
[ 9609.976663] sd 8:0:0:0: [sdc] Write Protect is off
[ 9609.976667] sd 8:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 9609.976670] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.978667] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.978673]  sdc: sdc1
[ 9609.984165] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.984172] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 9624.378814] usb 1-6: USB disconnect, address 8
[ 9624.836027] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 9624.969891] usb 1-6: configuration #1 chosen from 1 choice
[ 9624.973715] scsi9 : SCSI emulation for USB Mass Storage devices
[ 9624.973853] usb-storage: device found at 10
[ 9624.973855] usb-storage: waiting for device to settle before scanning
[ 9625.478557] usb 1-5: USB disconnect, address 9
[ 9625.604038] usb 1-6: USB disconnect, address 10
[ 9625.880031] usb 1-6: new high speed USB device using ehci_hcd and address 11
[ 9626.013886] usb 1-6: configuration #1 chosen from 1 choice
[ 9626.015714] scsi10 : SCSI emulation for USB Mass Storage devices
[ 9626.015909] usb-storage: device found at 11
[ 9626.015912] usb-storage: waiting for device to settle before scanning
[ 9626.726062] usb 1-6: USB disconnect, address 11
```

And after inserting the audio cd that does work:

```
[ 9609.969444] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[ 9609.969876] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 9609.976190] sd 8:0:0:0: [sdc] 3940351 512-byte logical blocks: (2.01 GB/1.87 GiB)
[ 9609.976663] sd 8:0:0:0: [sdc] Write Protect is off
[ 9609.976667] sd 8:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 9609.976670] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.978667] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.978673]  sdc: sdc1
[ 9609.984165] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 9609.984172] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 9624.378814] usb 1-6: USB disconnect, address 8
[ 9624.836027] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 9624.969891] usb 1-6: configuration #1 chosen from 1 choice
[ 9624.973715] scsi9 : SCSI emulation for USB Mass Storage devices
[ 9624.973853] usb-storage: device found at 10
[ 9624.973855] usb-storage: waiting for device to settle before scanning
[ 9625.478557] usb 1-5: USB disconnect, address 9
[ 9625.604038] usb 1-6: USB disconnect, address 10
[ 9625.880031] usb 1-6: new high speed USB device using ehci_hcd and address 11
[ 9626.013886] usb 1-6: configuration #1 chosen from 1 choice
[ 9626.015714] scsi10 : SCSI emulation for USB Mass Storage devices
[ 9626.015909] usb-storage: device found at 11
[ 9626.015912] usb-storage: waiting for device to settle before scanning
[ 9626.726062] usb 1-6: USB disconnect, address 11
[10929.985236] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10929.985243] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10929.985249] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[10929.985256] end_request: I/O error, dev sr0, sector 0
[10929.985261] Buffer I/O error on device sr0, logical block 0
[10929.985267] Buffer I/O error on device sr0, logical block 1
[10929.985271] Buffer I/O error on device sr0, logical block 2
[10929.985274] Buffer I/O error on device sr0, logical block 3
[10929.985277] Buffer I/O error on device sr0, logical block 4
[10929.985280] Buffer I/O error on device sr0, logical block 5
[10929.985284] Buffer I/O error on device sr0, logical block 6
[10929.985287] Buffer I/O error on device sr0, logical block 7
[10929.985290] Buffer I/O error on device sr0, logical block 8
[10929.988903] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10929.988908] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10929.988913] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[10929.988922] end_request: I/O error, dev sr0, sector 0
[10930.503025] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10930.503031] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10930.503037] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[10930.503044] end_request: I/O error, dev sr0, sector 0
[10930.504107] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10930.504112] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10930.504117] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[10930.504123] end_request: I/O error, dev sr0, sector 0
[10930.506534] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10930.506539] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10930.506544] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[10930.506550] end_request: I/O error, dev sr0, sector 0
```
Does this help in anything?

---

### Post by olig1905 on 2010-05-06
This sounds like the same problem as i am having! 

I do not want to start a new thread...

do you still have this problem? 
If it was solved how?

and did the disks not spin at all?

i havent got a disk that works as far as ive tested here is my dmesg:

```
[ 3076.230034] floppy0: floppy timeout called
[ 3076.230039] PM: resume of drv:floppy dev:floppy.0 complete after 2999.939 msecs
[ 3076.560009] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[ 3076.937022] PM: resume of drv:usb dev:2-2 complete after 706.936 msecs
[ 3076.937036] sd 1:0:0:0: [sda] Starting disk
[ 3077.005753] ndiswrapper: using IRQ 16
[ 3077.220015] PM: resume of drv:ndiswrapper dev:0000:02:00.0 complete after 215.690 msecs
[ 3077.220086] PM: resume of devices complete after 5379.670 msecs
[ 3077.220177] PM: resume devices took 5.380 seconds
[ 3077.220199] PM: Finishing wakeup.
[ 3077.220200] Restarting tasks ... done.
[ 3078.302384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3078.305019] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[ 3078.305526] eth0: no link during initialization.
[ 3078.305694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3093.351101] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3093.366451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3104.120430] wlan0: no IPv6 routers present
[ 3419.844499] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 3419.849162] SGI XFS Quota Management subsystem
[ 3419.913377] JFS: nTxBlock = 8192, nTxLock = 65536
[ 3420.080769] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 3420.225329] QNX4 filesystem 0.2.3 registered.
[ 3420.465881] Btrfs loaded

```

BUMPING THIS THREAD IN DIRE NEED OF HELP

Thankyou to all who can help:p

---

### Post by Lrpbpb on 2010-05-08
> do you still have this problem? 
If it was solved how?

and did the disks not spin at all?I'm no linux expert so I have no idea how to help you with the dmesg. 

However, I did manage to solve the problem. I just did a fresh install of 10.04 Lucid Lynx (download at: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) and after installing the restricted extras (Ubuntu Software center-> Then search for Ubuntu Restricted Extras-> download) and now it reads all types of disks, from copyright dvd to my own burned disks, music, etc. Hope this helps ;)

PS: Besides, lucid is much better than karmic

---

