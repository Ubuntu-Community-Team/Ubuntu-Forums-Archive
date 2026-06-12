---
title: "Can't mount MP3 player Archos 3 Vision"
date: 2010-01-10
forum: Hardware
---

### Post by simsimon on 2010-01-10
Hi,

One of my friends who is using Ubuntu 8.04 bought a Archos 3 vision recently.
I told him that it would work with Ubuntu because according to the Archos' Website this mp3 player is recognised as a mass storage media.

But when he plugs the device in a usb port he gets nothing.
I told him to try different cables and usb ports but nothing changed. 
Then he tried with a laptop running windows and it worked. 


When he plugs the device and I run a lsusb (I remotly control his computer with ssh) I see this a few seconds 
```
root@miko:~# lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04b8:0849 Seiko Epson Corp. Stylus SX205
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 012: ID 071b:3203 Domain Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
```


but it dispears quickly
```
root@miko:~# lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04b8:0849 Seiko Epson Corp. Stylus SX205
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
```


a dmesg now :
```

[ 8727.134762] usb 3-1: new high speed USB device using ehci_hcd and address 12
[ 8727.270003] usb 3-1: configuration #1 chosen from 1 choice
[ 8727.270242] scsi21 : SCSI emulation for USB Mass Storage devices
[ 8727.270438] usb-storage: device found at 12
[ 8727.270442] usb-storage: waiting for device to settle before scanning
[ 8732.265492] usb-storage: device scan complete
[ 8732.265868] scsi 21:0:0:0: Direct-Access              Archos3          1.00 PQ: 0 ANSI: 0
[ 8732.276343] sd 21:0:0:0: [sdc] 15857664 512-byte hardware sectors (8119 MB)
[ 8732.385362] usb 3-1: reset high speed USB device using ehci_hcd and address 12
[ 8732.573554] usb 3-1: USB disconnect, address 12
[ 8732.573726] sd 21:0:0:0: [sdc] Write Protect is off
[ 8732.573729] sd 21:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 8732.573732] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[ 8732.574310] sd 21:0:0:0: [sdc] READ CAPACITY failed
[ 8732.574314] sd 21:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 8732.574318] sd 21:0:0:0: [sdc] Sense not available.
[ 8732.574602] sd 21:0:0:0: [sdc] Write Protect is off
[ 8732.574605] sd 21:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 8732.574607] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[ 8732.575083] sd 21:0:0:0: [sdc] READ CAPACITY failed
[ 8732.575086] sd 21:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 8732.575090] sd 21:0:0:0: [sdc] Sense not available.
[ 8732.575383] sd 21:0:0:0: [sdc] Write Protect is off
[ 8732.575386] sd 21:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 8732.575388] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[ 8732.575469] sd 21:0:0:0: [sdc] Attached SCSI removable disk
[ 8732.575510] sd 21:0:0:0: Attached scsi generic sg3 type 0


```



Does anyone know what the problem is ?

---

### Post by simsimon on 2010-01-17
up !

---

### Post by karlrelton on 2011-05-13
It depends what version of Ubuntu you have installed. Its been working fine in Maverick and Lynx, though there is now a regression in Natty (but that has been spotted upstream).

---

### Post by coffeecat on 2011-05-13
> **karlrelton said:**
> though there is now a regression in Natty (but that has been spotted upstream).

Here's the bug report for Ubuntu Natty on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227)

I'm glad to hear it's been picked up upstream. Out of interest, what package is the bug in?

---

### Post by Dale61 on 2011-05-14
I have a 1st generation iPod shuffle, and it hasn't been recognised since 10.04.  I spent an age trying to get it to work in 10.10, but gave that up as a bad joke.  I haven't even bothered with 11.04.

What I do now is that I have all my music on a flash drive, I plug that in to my defacto's Vista laptop, delete the old playlist, drag-and-drop a new set of tracks, then remove both.  Quite simple really.

---

