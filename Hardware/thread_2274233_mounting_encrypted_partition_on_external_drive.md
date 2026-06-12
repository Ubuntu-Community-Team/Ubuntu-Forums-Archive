---
title: "mounting encrypted partition on external drive"
date: 2015-04-18
forum: Hardware
---

### Post by janl162 on 2015-04-18
I'm trying to mount the disk from my old computer as a USB drive so I can transfer the data to my new computer.

The complication is that my data is on an encrypted partition.

When I attempt to open the partition it comes up with the file manager showing my home folder, and when I try to open my home folder on that drive it comes up with icons labled "Access Your Private Data Desktop" and README.TXT.  The README file says:

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

clicking on "Access Your Private Data" momentarially opens a terminal window and (as near as I can tell) does nothing.

Manually opening a terminal window and running  ecryptfs-mount-private does noting, not even an error message.

I've followed some other instructions, but I can't figure out what the name of the USB disk is, which those instructions need (I think.)

I do have the 32 hex digit key for the data, but where to put it?

any help is apprciated.

---

### Post by dino99 on 2015-04-19
when the usb disk is plugged, 'sudo blkid' or 'lshw -ls' will list it

---

