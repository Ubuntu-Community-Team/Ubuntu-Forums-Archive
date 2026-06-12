---
title: "sdb: unknown partition table"
date: 2008-07-16
forum: General Help
---

### Post by claralt on 2008-07-16
hello everyone

I was using my pen drive to copy some files from a computer using Ubuntu and without any reason the computer crashed, i turned it of and took off the usb drive. from that day until now i can't open the USB drive, windows tells me i have to format the pen, and 1 sec later tells me "Windows can't format the drive" or something. Linux tells me it can't mount the drive.

I open the terminal and i wrote

tail -f /var/log/messages

when i plug in the pen drive it says:


Jul 16 23:19:03 clara kernel: [ 6842.465527] usb 5-8: new high speed USB device using ehci_hcd and address 14
Jul 16 23:19:03 clara kernel: [ 6842.598387] usb 5-8: configuration #1 chosen from 1 choice
Jul 16 23:19:03 clara kernel: [ 6842.598829] scsi15 : SCSI emulation for USB Mass Storage devices
Jul 16 23:19:08 clara kernel: [ 6847.589693] scsi 15:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2
Jul 16 23:19:08 clara kernel: [ 6847.592906] sd 15:0:0:0: [sdb] 16384001 512-byte hardware sectors (8389 MB)
Jul 16 23:19:08 clara kernel: [ 6847.593649] sd 15:0:0:0: [sdb] Write Protect is off
Jul 16 23:19:08 clara kernel: [ 6847.596142] sd 15:0:0:0: [sdb] 16384001 512-byte hardware sectors (8389 MB)
Jul 16 23:19:08 clara kernel: [ 6847.596641] sd 15:0:0:0: [sdb] Write Protect is off
Jul 16 23:19:08 clara kernel: [ 6847.596650]  sdb: unknown partition table
Jul 16 23:19:08 clara kernel: [ 6847.603720] sd 15:0:0:0: [sdb] Attached SCSI removable disk
Jul 16 23:19:08 clara kernel: [ 6847.603763] sd 15:0:0:0: Attached scsi generic sg2 type 0



when I plug it off this is the message;


Jul 16 23:19:12 clara kernel: [ 6852.075445] usb 5-8: USB disconnect, address 14

something is wrong with the partion table... i think but i am unable to resolve the problem, can anyone help me?

---

### Post by tassoman on 2009-10-13
I got same error with a friend's pen drive ... using cfdisk on it gives back unreversible error.

I think that usb key has gone for good ... farewell :-({|=

---

### Post by az on 2009-10-13
It's probably too late, but a failed drive like that could be recoverable.

Use software like gnu-ddrescue to image the drive and then try to either repair the partition table and filesystem(s) on it or use data-carving software to pull the files from the image without using the filesystem.

help.ubuntu.com/community/DataRecovery

---

### Post by sixerjman on 2012-01-11
Just came across this (I know it's probably too late), but this
post

[http://forums.gentoo.org/viewtopic-t-797418.html](http://forums.gentoo.org/viewtopic-t-797418.html)

suggested to run 'update-usbids' and the drive was recognized after that, at least enough to run cfdisk and create a partition table.

---

### Post by oldos2er on 2012-01-11
Closed, necromancy.

---

