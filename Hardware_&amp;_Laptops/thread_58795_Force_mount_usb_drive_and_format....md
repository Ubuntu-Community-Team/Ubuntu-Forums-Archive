---
title: "Force mount usb drive and format..."
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by orev on 2005-08-21
I have a USB drive that I can not seem to get mounted.  The drive is a ARCHOS Jukebox w/20GB drive.

I can not get the drive to mount, or even get kubuntu to even see it.

The drive is messed up somehow...but I would think that I could mount it somehow, and reformat the drive.

the drive should be at /dev/sda1/

Any suggestions?

---

### Post by nad on 2005-08-21
Once you have plugged in your drive, run the command: dmesg | tail  to see what has happened.

Many USB mass storage ddevices need to be partitioned and have a FAT filesystem made with a _standard_ implementation in order to be used with an operating system other than the one it is designed for.

---

### Post by orev on 2005-08-21
I ran that, and:

jason@HPDESKTOP:~$ dmesg | tail
usb-storage: device found at 15
usb-storage: waiting for device to settle before scanning
usb 5-5: reset high speed USB device using ehci_hcd and address 15
scsi: Device offlined - not ready after error recovery: host 15 channel 0 id 0 lun 0
usb-storage: device scan complete
usb 5-5: USB disconnect, address 15
usb 5-5: new high speed USB device using ehci_hcd and address 16
scsi16 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 16
usb-storage: waiting for device to settle before scanning
jason@HPDESKTOP:~$

any suggestions?

Thanks!

---

### Post by mcduck on 2005-08-22
To reformat the drive you don't want to mount it. Just make sure that it's _not_mounted_, and run 'sudo fdisk /dev/sda1/', delete existing partition and create a new one with fat32/vfat.

---

### Post by orev on 2005-08-22
"To reformat the drive you don't want to mount it. Just make sure that it's _not_mounted_, and run 'sudo fdisk /dev/sda1/', delete existing partition and create a new one with fat32/vfat."

I have been there before...and I get:

Unable to open /dev/sda1/
jason@HPDESKTOP:~$


That is why I thought I had to try to "force" mount it somehow...

Any suggestions?

---

### Post by nad on 2005-08-23
Something is not right (but you know that).

I'm familiar with addressing and IRQ issues caused by buggy bios'es (most notably with VIA chipsets), but, your error message "Device offlined - not ready after error recovery" would indicate another problem. Anybody else here ever mounted an ARCHOS Jukebox?

You may try tweaking your bios USB and IRQ settings and/or your boot parameters ( [http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO) ), howvever, sometimes it just won't work.

---

### Post by orev on 2005-08-24
The story is:  I bought this thing a couple of years ago, then got an iPod - gave the Jukebox to my brother.  I actually sucked (USB) about 15GB of music off of the device into kubuntu before I gave it to him.  It seemed to work fine.

He got it, tried to connect it to a WindowsXP box to get the same mp3s - Winslows told him that the device needed to be reformatted to be able to be used in Windows, he clicked OK, Windows attempted to do its thing, stopped in the middle of the "format", and we havent been able to access the device from WinXP or kubuntu since.

Maybe WinXP roached it?  Maybe the 'format" wiped some software required to access the HD?

I though that it should be pretty easy, just a 20GB Hitachi IDE laptop HD plugged into a board...

I think it may be written off...

---

### Post by nad on 2005-08-25
This happened to me with an OTi Cigar Drive circa 2002.

fdisk.exe fixed it. After I found that I just couldn't access the device, this was the only editor that worked. I must have done it from a DOS window in WIN98.

---

### Post by mcduck on 2005-08-25
Have you switched of all automounting etc. for USB-drives? Possibly your system is still trying to automount the drive.. After that try fdisk again.

---

