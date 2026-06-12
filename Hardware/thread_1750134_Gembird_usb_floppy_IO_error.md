---
title: "Gembird usb floppy I/O error"
date: 2011-05-05
forum: Hardware
---

### Post by Diederick on 2011-05-05
Good day,


I bought a Gembird USB floppy device a while ago. It took me some time to figure out how to mount and all (I'm relatively new to this stuff) but it worked just fine.

Now, for some reason when I plug in the USB floppy it just sits there, motor spinning, LED on. When I view *dmesg*, I get this (might not be complete / contain other stuff?):
```
[ 6408.493366] sd 17:0:0:0: [sdc] READ CAPACITY failed
[ 6408.493368] sd 17:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6408.493372] sd 17:0:0:0: [sdc] Sense not available.
[ 6408.493386] sd 17:0:0:0: [sdc] Assuming drive cache: write through
[ 6408.493389] sd 17:0:0:0: [sdc] Attached SCSI removable disk
[ 6426.904012] usb 2-8: new full speed USB device using ohci_hcd and address 15
[ 6427.116219] usb 2-8: configuration #1 chosen from 1 choice
[ 6427.119654] scsi18 : SCSI emulation for USB Mass Storage devices
[ 6427.119801] usb-storage: device found at 15
[ 6427.119803] usb-storage: waiting for device to settle before scanning
[ 6432.116550] usb-storage: device scan complete
[ 6432.136386] scsi 18:0:0:0: Direct-Access     TEAC     USB UF000x       4.00 PQ: 0 ANSI: 0 CCS
[ 6432.136960] sd 18:0:0:0: Attached scsi generic sg3 type 0
[ 6432.320015] usb 2-8: reset full speed USB device using ohci_hcd and address 15
[ 6432.648384] sd 18:0:0:0: [sdc] Attached SCSI removable disk
[ 6450.185198] sd 18:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[ 6450.217222] sd 18:0:0:0: [sdc] Write Protect is on
[ 6450.217224] sd 18:0:0:0: [sdc] Mode Sense: 00 46 02 80
[ 6450.217226] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6450.313205] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[ 6450.313210]  sdc:
[ 6458.186090] sd 18:0:0:0: [sdc] Unhandled sense code
[ 6458.186093] sd 18:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6458.186096] sd 18:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 6458.186100] sd 18:0:0:0: [sdc] Add. Sense: Incompatible medium installed
[ 6458.186104] sd 18:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00 00 00
[ 6458.186112] **end_request: I/O error, dev sdc, sector 0**
[ 6458.186116] **Buffer I/O error on device sdc, logical block 0**
```*lsusb*:
```
**Bus 002 Device 015: ID 0644:0000 TEAC Corp. Floppy**
Bus 002 Device 020: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 017: ID 1532:0101 Razer USA, Ltd Copperhead Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```(bold = floppy device)


Yesterday I was able to get the device to work - sometimes. After a lot of plugging in/out dmesg gave no error and I was able to mount it and read/write data to the floppy. After a while it stopped working again.

I plugged it in on a Windows 2000 laptop and it showed up in the device list, but it says the floppy must be formatted. The build-in floppy drive is able to read/write from/to that floppy, though.

Now, my question: does this mean the device is broken? I mean, obviously there is something going on, and it 'makes sense' for the device to be broken. I'd hate to buy a new one, this one is around 3 months old and I've used it +/- 50 times to write data to a floppy...



I'm running Ubuntu 10.04 LTS (Lucid Lynx). [link to the Gembird page.]("http://www.gembird.nl/default.aspx?op=products&op2=item&id=2877")



Thanks in advance,
DDK

---

### Post by Joe of loath on 2011-05-05
Looks dead to me. Have you tried a different floppy?

Also, why are you still using floppy? That's so last century :lol:

---

### Post by Diederick on 2011-05-05
Hello Joe,


Yes, I've tried 4 floppies. Point is, even when I plug the device in with no floppy, it still gives the I/O error.


Last century - so true. But I'm writing an 'OS' (nothing fancy, just the 'basics') and I couldn't get Bochs (emulator) to boot from an USB drive. So, back to using a floppy. Besides, I just *love* the sound the floppy drive makes :wink:.

---

### Post by Joe of loath on 2011-05-05
Yeah, sounds like it's dead, then. Sometimes these things happen, especially since they're mechanical devices. Maybe contact the shop for a refund or replacement?

Good luck with your OS project :D Have you tried any other emulators, or do you need Bochs for the architecture you're coding for? Or, you could create a virtual floppy by creating a disk image and formatting it as a floppy (I've done it before, not too hard).

(And true dat about the sound. Until you try transfer a 1.4mb file from the disk and it takes a couple of minutes :lol:)

---

