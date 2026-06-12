---
title: "USB not detected on Gutsby but detected on XP..."
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by dmick on 2008-02-11
Ubuntu Gutsby can't detect my USB key whereas there is no pb on windows XP.
I read several messages (I didn't want to use your time for nothing!) but only found a post about a utility command: "tail -f /var/log/messages". So when I typed it, here is what is written:
_________________________________

Feb 11 16:45:39 pc244-41 kernel: [  380.431544] usb 5-8: new high speed USB device using ehci_hcd and address 7
Feb 11 16:45:39 pc244-41 kernel: [  380.576523] usb 5-8: configuration #1 chosen from 1 choice
Feb 11 16:45:39 pc244-41 kernel: [  380.576699] hub 5-8:1.0: USB hub found
Feb 11 16:45:39 pc244-41 kernel: [  380.576803] hub 5-8:1.0: 1 port detected
Feb 11 16:45:39 pc244-41 kernel: [  380.879576] usb 5-8.1: new high speed USB device using ehci_hcd and address 8
Feb 11 16:45:39 pc244-41 kernel: [  380.984622] usb 5-8.1: configuration #1 chosen from 1 choice
Feb 11 16:45:39 pc244-41 kernel: [  380.984850] scsi7 : SCSI emulation for USB Mass Storage devices
Feb 11 16:45:44 pc244-41 kernel: [  385.983089] scsi 7:0:0:0: Direct-Access     Corsair  Flash Voyager    1.00 PQ: 0 ANSI: 0 CCS
Feb 11 16:45:44 pc244-41 kernel: [  385.984444] sd 7:0:0:0: [sdc] 2031616 512-byte hardware sectors (1040 MB)
Feb 11 16:45:44 pc244-41 kernel: [  385.987567] sd 7:0:0:0: [sdc] Write Protect is off
Feb 11 16:45:44 pc244-41 kernel: [  385.989816] sd 7:0:0:0: [sdc] 2031616 512-byte hardware sectors (1040 MB)
Feb 11 16:45:44 pc244-41 kernel: [  385.992939] sd 7:0:0:0: [sdc] Write Protect is off
Feb 11 16:45:44 pc244-41 kernel: [  385.992947]  sdc: sdc1
Feb 11 16:45:44 pc244-41 kernel: [  385.993741] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Feb 11 16:45:44 pc244-41 kernel: [  385.993779] sd 7:0:0:0: Attached scsi generic sg3 type 0
Feb 11 16:45:44 pc244-41 kernel: [  386.103896] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 11 16:45:44 pc244-41 kernel: [  386.103905] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
Feb 11 16:45:44 pc244-41 kernel: [  386.103910] sd 7:0:0:0: [sdc] Add. Sense: Unrecovered read error
Feb 11 16:45:44 pc244-41 kernel: [  386.103916] end_request: I/O error, dev sdc, sector 16

------------(....the same last 4 lines many times... and finally: )------------------
Feb 11 16:46:15 pc244-41 kernel: [  416.186302] usb 5-8.1: reset high speed USB device using ehci_hcd and address 8
Feb 11 16:46:45 pc244-41 kernel: [  446.342809] usb 5-8.1: reset high speed USB device using ehci_hcd and address 8
_________________________________

I would be *very* grateful if anyone can help.

Michael

---

### Post by chadeldridge on 2008-02-11
If you have been moving the device back and forth from Windows to Unix consoles I would suggest putting it back in the Windows box and properly dismounting the flash drive.  Then try your linux box again.  Also what file format is the key in?

---

### Post by dmick on 2008-02-12
First thank you for your help. 
Second, I am sorry but I don't really understand what you mean by "box" and "console". I don't have any emulators of Windows or Linux on each respective OS so they are totally independent and I don't understand when you told me to "put [the USB key] back in the Windows box and properly dismounting the flash drive, then try [my] linux box again". My USB key is a "1Gb Corsair Voyager Flash" which was formatted in FAT. I formatted in FAT32 under windows but it didn't change anything,
The USB is still not recognized at all by Ubuntu... Thank you for your help!

---

### Post by dmick on 2008-02-12
Problem solved ! (At least for now)

In fact I looked at another thread somewhere on Internet, on the solution, specific to the CORSAIR VOYAGER FLASH usb key, was to download the corsair utility to format it (apparently it's different from a standard formatting).

So if anyone has this problem, just download the utility at [http://www.houseofhelp.com/forums/showthread.php?t=53660](http://www.houseofhelp.com/forums/showthread.php?t=53660) and format it under windows. It should be fine afterwards !

Michael

---

