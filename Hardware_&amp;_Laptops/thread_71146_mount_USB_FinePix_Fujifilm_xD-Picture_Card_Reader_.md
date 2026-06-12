---
title: "mount USB FinePix Fujifilm xD-Picture Card Reader card"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by Skara on 2005-10-02
Alright, I've got a Fujifilm FinePix image memory card reader (dpc-r1).
I need to know how to mount it. ^^;

I really don't know where to begin.

---

### Post by Skara on 2005-10-02
Erhm.. Ok, I think I know why I'm confused at least.  When you plug in some kind of usb drive, does it not add something in /dev?
Device Manager picks it up, but there's no /dev/???.

What the heck do I do?

---

### Post by mkoyle on 2006-11-08
It looks like your device is supported by a driver in some kernels... it is listed at [http://alauda.sourceforge.net/](http://alauda.sourceforge.net/) as one of the devices supported by the driver.

What version of Ubuntu are you using?

Also, tell us what kernel you have: open a terminal and type 

uname -a


My output for Ubuntu Eft is the following:

Linux ruth 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Knowing this information, we can move forward.  If you have a kernel newer than 2.6.15, I believe this should be automatically detected and mounted as you were saying at /dev/sda (the a could be any letter, depending on how many SCSI/SATA/USB devices you have installed) when there is a disk inserted.  

Keep looking around if you haven't fixed this.  The fellow making 'alaudia' drivers should have this up and working, so somwhere on the web there is a solution.

--Matthew

---

### Post by andrewPCT on 2007-02-01
After searching the forums, this appears to be the only thread on the Fujifilm FinePix DPC-R1.  I am trying to get mine working.

$ uname -a
Linux random 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
(Ubuntu 6.10)

Any help would be nice.

---

### Post by rykel on 2007-02-23
I would be interested to know the answers to this thread too, as I also deal with xD cards etc...

---

### Post by ecspike on 2007-02-27
I'm sure it will be fine once Feisty comes out. I was previously running Dapper and having the same problems. Once I upgrade to Feisty Herd 4, it was able to read the camera without any problems.

** Feisty is not production yet. Upgrade at your own risk.

---

### Post by andrewPCT on 2007-02-27
I hope so, btw, this isn't a camera, just a card reader ( [http://www.alphalion.com/images/dpcr1.jpg](http://www.alphalion.com/images/dpcr1.jpg) )

---

### Post by thom83 on 2007-03-03
When you plug in your card reader, is it empty or with a memory card in it?
When it is plugged in with a memory card, what is the result for :
		sudo fdisk -l		(minus L)

---

### Post by andrewPCT on 2007-03-03
When plugged in with a memory card, the only output from that command is about the harddrive. (no mention of the memory card/reader)

---

### Post by thom83 on 2007-03-03
And if you unplug and replug the reader card with a card in it, what is the result of 

dmesg | tail -n 20

---

### Post by andrewPCT on 2007-03-03
[17825998.572000] usb 5-7.1: new full speed USB device using ehci_hcd and address 7
[17825998.688000] usb 5-7.1: configuration #1 chosen from 1 choice
[17825998.688000] usb-storage: probe of 5-7.1:1.0 failed with error -5
[17826078.240000] usb 5-7.1: USB disconnect, address 7
[17828730.448000] usb 5-7.1: new full speed USB device using ehci_hcd and address 8
[17828730.556000] usb 5-7.1: configuration #1 chosen from 1 choice
[17828730.556000] usb-storage: probe of 5-7.1:1.0 failed with error -5
[17828747.400000] usb 5-7.1: USB disconnect, address 8

---

### Post by thom83 on 2007-03-03
Maybe your memory card is new and not formated.
When you plug in your finepix camera, you see it as /media/sd?. Is'n'it?

---

### Post by andrewPCT on 2007-03-03
My camera is an Olympus camera.  The memory card does have photos on it. (Works fine on my windows computer.)

(Ubuntu 6.10)

---

### Post by thom83 on 2007-03-03
Je nage! I don't see where is the problem. When you typ

lsusb

what is the output?

---

### Post by andrewPCT on 2007-03-03
$ lsusb 
Bus 005 Device 009: ID 0584:0008 RATOC System, Inc. 
Bus 005 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 002 Device 001: ID 0000:0000  


I see no mention of it.

---

### Post by thom83 on 2007-03-03
It is out of my competence...
I found a link for the same problem :
[http://ubuntuforums.org/showthread.php?t=282179](http://ubuntuforums.org/showthread.php?t=282179)
Maybe you'll get a solution by reading these 5 pages.
Good luck and good night (it is 23:50 here).

---

### Post by andrewPCT on 2007-03-03
I was able to get it recognized in 7.04, but it only saw the SmartMedia slot, and not the xD slot.

---

### Post by ginnie6 on 2007-03-03
i use xd cards and have had no problem with my card reader being read. I have an olympus mausb-300 reader. When I put a crad in it it automatically mounts.

---

### Post by druidb on 2008-01-02
Hi all!

I've been reading some of the forum messages regarding this problem. I have a FUJI Finepix XD Card reader (looks like it was made by Myson Corp.)

I believe that I somehow unmounted the card reader but now when I plug the USB card reader into the PC it does not come up as FINEPIX any loner but as "Myson CS8819A2-109  0".

Right-clicking on the icon for the drive and selecting "Mount Volume" comes up with an error: "Unable to mount media. There is probably no media in the drive."

Inserting the XD card into my Finepix camera is successful as I can see all the photos.

uname -a:
Linux brett-ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

dmesg:
[  798.184000] usb 7-1: configuration #1 chosen from 1 choice
[  798.184000] scsi7 : SCSI emulation for USB Mass Storage devices
[  798.184000] usb-storage: device found at 6
[  798.184000] usb-storage: waiting for device to settle before scanning
[  803.184000] usb-storage: device scan complete
[  803.184000] scsi 7:0:0:0: Direct-Access     Myson    CS8819A2-109  0  1.01 PQ: 0 ANSI: 0 CCS
[  803.184000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  803.184000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  960.112000] ata1.00: exception Emask 0x2 SAct 0x2 SErr 0x0 action 0x2 frozen
[  960.112000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x2 FIS=004040a1:00000001)
[  960.112000] ata1.00: cmd 61/08:08:83:ab:86/00:00:0f:00:00/40 tag 1 cdb 0x0 data 4096 out
[  960.112000]          res 40/00:08:83:ab:86/00:00:0f:00:00/40 Emask 0x2 (HSM violation)
[  960.424000] ata1: soft resetting port
[  960.596000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  960.596000] ata1.00: configured for UDMA/133
[  960.596000] ata1: EH complete
[  960.596000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  960.596000] sd 0:0:0:0: [sda] Write Protect is off
[  960.596000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  960.596000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
=========================
Any ideas?

---

### Post by rykel on 2008-01-03
Hi all,

I noticed that on Gutsy Gibbon, my card reader works (almost) perfectly... it could automount SD cards, but NOT the Fujifilm xD cards.

---

