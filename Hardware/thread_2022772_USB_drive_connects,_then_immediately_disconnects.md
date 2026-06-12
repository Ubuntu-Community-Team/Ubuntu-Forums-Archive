---
title: "USB drive connects, then immediately disconnects"
date: 2012-07-11
forum: Hardware
---

### Post by argo82 on 2012-07-11
Hi,
I have a usb pen drive that suddenly stopped being recognized in Ubuntu and Windows. It starts flashing after being plugged in, but after a few seconds the led goes out. It doesn't show up in Windows' partition manager. In Ubuntu, syslog says
> Jul 11 18:36:46 ubuntu kernel: [  514.070039] usb 2-6: new high speed USB device using ehci_hcd and address 6
Jul 11 18:36:46 ubuntu kernel: [  514.221541] usb 2-6: configuration #1 chosen from 1 choice
Jul 11 18:36:46 ubuntu kernel: [  514.221789] scsi15 : SCSI emulation for USB Mass Storage devices
Jul 11 18:36:46 ubuntu kernel: [  514.222017] usb-storage: device found at 6
Jul 11 18:36:46 ubuntu kernel: [  514.222021] usb-storage: waiting for device to settle before scanning
Jul 11 18:36:47 ubuntu kernel: [  514.691698] usb 2-6: USB disconnect, address 6

I tried different ports on different computers, therefore I assume there is a problem with the device. I'm afraid it's broken :(, but maybe someone has an idea what I can try to revive it?
Thanks in advance!
argo82

---

### Post by gopherkiler9 on 2012-07-12
well if youve tried it in multiple ports on various computers, odds are it IS the pen drive. If you are hoping to salvage it, you could take a nice close peek at the pins within the usb head. make sure things are as they are supposed to be (clean and not broke). at WORST case scenario, pop the bad boy open and make sure all is well within the drive.

I'm assuming there are valuable materials on that drive, which is why this is so heart breaking for you, so I am assuming formatting is not an option. If it is however, give it a try. Just make sure that you are formatting it to the correct type like ntfs, fat32, etc.

you CAN re-solder any broken bits if possible... just be careful.


my first method of fixing would be to look at the usb.. if all looks well, reformat it if possible.

---

### Post by americanman28 on 2012-07-12
The drive could be dying

---

