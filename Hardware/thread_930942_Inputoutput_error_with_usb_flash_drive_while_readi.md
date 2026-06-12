---
title: "Input/output error with usb flash drive while reading/writing on laptop"
date: 2008-09-26
forum: Hardware
---

### Post by bj0 on 2008-09-26
I came across this problem while trying to create an Ubuntu live USB on my laptop.  The hardware involved is:

Corsair Flash Voyager, 16 GB.
Sony Vaio PCG-NVR23

When I first plug the usb drive into the laptop, it is detected and mounted automatically.  I can even boot off of it using qemu.  When I try to copy files to/from it, however, it works fine for a little bit and then just halts with "Input/output error".  When this happens, the device disappears from the mount list and I can't even see it with 'sudo fdisk -l' anymore.  Unplugging it and plugging it back in has no effect, but if I reboot the laptop, it is working fine again (until I try to read/write, then the behavior repeats).

This only happens on this laptop, I can use the usb drive fine from my desktop pc (booted up with ubuntu 8.04 live cd) with no errors.

I've searched a little bit but can't seem to find anyone else with this same problem (specifically the usb device becoming unusable until rebooting).  If anyone has any information about this, or something to test, let me know.

B

---

### Post by Pha[N]toM on 2008-10-13
[COLOR="Red"]**It's doubling of the theme.**[/COLOR]

Hello, I have some different problem. Today i've buy 16Gb USB-flash Drive from Corsair.

When I put it into my laptop he (USB-FLASH, may-be "she") blinks his blue diode and not automounts onto system (Ubuntu 8.04.1, x86-64)

dmesg, after putting flash-stick in to the usb-hole tells:
```
[15018.849872] usb 6-1: new high speed USB device using ehci_hcd and address 6
[15018.987834] usb 6-1: configuration #1 chosen from 1 choice
[15019.006898] scsi9 : SCSI emulation for USB Mass Storage devices
[15019.013826] usb-storage: device found at 6
[15019.013831] usb-storage: waiting for device to settle before scanning
[15024.005605] usb-storage: device scan complete
[15024.006841] scsi 9:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[15024.018061] sd 9:0:0:0: [sdb] 32112640 512-byte hardware sectors (16442 MB)
[15024.019066] sd 9:0:0:0: [sdb] Write Protect is off
[15024.019073] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[15024.019075] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[15024.022287] sd 9:0:0:0: [sdb] 32112640 512-byte hardware sectors (16442 MB)
[15024.023286] sd 9:0:0:0: [sdb] Write Protect is off
[15024.023290] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[15024.023292] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[15024.023298]  sdb: sdb1
[15024.075216] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[15024.075260] sd 9:0:0:0: Attached scsi generic sg2 type 0

```:?:

when I ```
 sudo mount -t vfat -o user /dev/sdb1 /media/fat

```
I've got a mounted flash-drive, but I can't write into it. 

Waiting for Help! Thanx! And..... sorry for my eagly english :)

---

### Post by Pha[N]toM on 2008-10-13
So... my problem... it really [COLOR="Red"]**solved**[/COLOR].
I use gparted. For first I've format flash drive in ReiserFS, put it away and put it back in the (usb)hole. Flash drive has mounted in RW-mode, I test it, all is OK (and writing >2Gb files). 
Today morning, I've format it to the FAT32, remove and put back and it works fine!
(I try to write files, larger than 2Gb, and they are writes correctly...)

---

### Post by bj0 on 2008-11-23
I just tried to use this laptop again, it's been a little while but I am still getting this same problem.  I tried to copy large files from my main pc to this one using the usb stick, but it keeps failing.

Anyone have any ideas?

---

### Post by bj0 on 2009-03-15
So I tried to copy some pictures from a sony camera via usb to the laptop in question, the error still presents.

Maybe I should make a bug report?

---

