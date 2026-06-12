---
title: "64GB usb key disk is unreadable on ubuntu"
date: 2011-05-23
forum: Hardware
---

### Post by karimone on 2011-05-23
Hi all, I friend of mine give me his usb to connect on my ubuntu, but there is no way to mount it. The key works perfectly on a Mac and the usb port works perfectly on my computer with ubuntu on.

Here the dmesg:
```
[ 4068.081517] usb 1-1.4: new high speed USB device using ehci_hcd and address 9
[ 4068.268756] usb 1-1.4: configuration #1 chosen from 1 choice
[ 4068.269146] scsi10 : SCSI emulation for USB Mass Storage devices
[ 4068.269265] usb-storage: device found at 9
[ 4068.269268] usb-storage: waiting for device to settle before scanning
[ 4073.248588] usb-storage: device scan complete
[ 4073.250389] scsi 10:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[ 4073.251629] sd 10:0:0:0: Attached scsi generic sg8 type 0
[ 4073.255904] sd 10:0:0:0: [sdh] 131072000 512-byte logical blocks: (67.1 GB/62.5 GiB)
[ 4073.256469] sd 10:0:0:0: [sdh] Write Protect is off
[ 4073.256474] sd 10:0:0:0: [sdh] Mode Sense: 03 00 00 00
[ 4073.256477] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 4073.258659] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 4073.258665]  sdh:
[ 4104.082677] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4135.057613] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4165.972722] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4196.888454] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4227.802816] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4258.693742] usb 1-1.4: reset high speed USB device using ehci_hcd and address 9
[ 4258.882461] sd 10:0:0:0: [sdh] Unhandled error code
[ 4258.882470] sd 10:0:0:0: [sdh] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 4258.882480] sd 10:0:0:0: [sdh] CDB: Read(10): 28 00 07 cf ff f8 00 00 01 00
[ 4258.882504] end_request: I/O error, dev sdh, sector 131071992
[ 4258.882514] Buffer I/O error on device sdh, logical block 16383999

```

Fdisk and Gparted freeze on finding device if the usb key is plugged on. What I can do?

---

### Post by TenPlus1 on 2011-05-23
Did your friend format the flash drive on his mac ? if so what filesystem did he use, THAT could be the problem...  While Ubuntu can easily see fat32 and ntfs flash drives he may have used a mac filesystem which has to be setup specifically for the device...

---

### Post by karimone on 2011-05-26
I copied everything now. But the key was unreadable from the ubuntu in every format (FAT, NTFS, HFS+). Everytime I formatted from the Mac because wasn't readable from ubuntu. So I used an external hard disk and I bring everything on the Mac, but what surprised me is that the key was really really slow on writing.

---

### Post by samMD on 2011-05-26
I think you needed to format from ubuntu I have Patriot 64GB which I believe is NTFS formatted so I can copy like files larger than 10 GB at a time

---

### Post by karimone on 2011-05-26
The problem was that from Ubuntu the key was completely unusable. I tried to format it in NTFS, but wasn't on the list of GParted!

---

### Post by psusi on 2011-05-26
So when you run sudo fdisk -l, you get no output at all?  Even if you wait a while?

---

### Post by Jorge Rama on 2011-07-18
I have the same problem with my 8 GB USB PEN DRIVE from Vodafone

sudo fdisk -l 

appears to block after displaying the fixed disk information

---

### Post by ghormax on 2011-12-16
I have the same problem with a 32GB stick:
 ```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0011:7788  
Bus 001 Device 009: ID 046d:080f Logitech, Inc. Webcam C120
Bus 001 Device 008: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 007: ID 04f9:01ea Brother Industries, Ltd 
Bus 001 Device 006: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0475:059b Relisys/Teco Information System 
Bus 001 Device 002: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
dmesg | tail
[53313.238737] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[53326.160028] usb 1-9: reset high speed USB device using ehci_hcd and address 11
[53326.376552] sd 10:0:0:0: [sdh] Unhandled error code
[53326.376556] sd 10:0:0:0: [sdh]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[53326.376559] sd 10:0:0:0: [sdh] CDB: Read(10): 28 00 03 8a 3f f8 00 00 01 00
[53326.376566] end_request: I/O error, dev sdh, sector 59391992
[53326.376569] Buffer I/O error on device sdh, logical block 7423999
[53357.136033] usb 1-9: reset high speed USB device using ehci_hcd and address 11
[53388.176022] usb 1-9: reset high speed USB device using ehci_hcd and address 11
[53419.216023] usb 1-9: reset high speed USB device using ehci_hcd and address 11

```

fdisk -l also freezes and cannot complete when the stick is plugged in. 

I tried the stick when it was new. It works fine on Windows and I formatted there to no avail. I have tried many different Ubuntu machines with different versions. It is not recognized by any.

---

### Post by madvinegar on 2012-01-03
Try in terminal as root:

*modprobe usb-storage*


then insert the usb disk and let us know what happens.

---

### Post by electricgolem on 2013-02-23
Same problem as original poster.
modprobe usb-storage did nothing. 
What to do?

---

### Post by electricgolem on 2013-02-23
oh well... solved my case:

The drive was a fake.
I was sold a substandard 8GB pen drive that was tampered with so as to show up as a 64GB on Mac/Win. 

I was a fool to trust the deal too good to be true.

---

### Post by sudodus on 2013-02-23
All USB pendrives don't have exactly the same interface. I guess the manufacturer checks that they work with the commercial operating systems, but forgets about linux. Sometimes they also forget about some computer model. I think it is not worth bothering too much about it. Give it to a 'Windows or Mac only user', get a new pendrive and avoid that brand and model in the future!

---

### Post by cgaie on 2013-05-07
After this command I was able to browse my 64 memory stick

---

### Post by cgaie on 2013-05-07
After this command *modprobe usb-storage* I was able to browse my 64 memory stick

---

