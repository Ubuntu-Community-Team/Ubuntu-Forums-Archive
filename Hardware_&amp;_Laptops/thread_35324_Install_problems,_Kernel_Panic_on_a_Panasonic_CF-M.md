---
title: "Install problems, Kernel Panic on a Panasonic CF-M32: Help!"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by clashxen on 2005-05-18
Hi all-
I'm a relative newbie, but I follow directions well. Here's the problem. I have a Panasonic CF-M32 Sub-notebook with no 'input' paths (no cd, no floppy, can't boot from usb). It is a P-166 with a 4Gb harddrive, and 32 MB of onboard RAM (expandable to 160MB). I really want to run a version of linux (preferably Ubuntu) with a GUI. My original plan was pull the drive and put it into my desktop and install from there. The install went smoothly so I reinstalled the drive back into the laptop and it won't boot. It will get as far as uncompressing the kernel and starting to load when it suffers from a kernel panic. Here's the output if I boot in recovery mode (Grub 1.5):

blah blah blah..
RAMDISK: Loading 423Kib [1 disk] into RAM disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
/bin/sh:error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory.
VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

Whereupon it hangs, unresponsive to any keystroke or the power button. Only hitting the hardware reset button on the bottom gets it to unlock (or pulling the battery...eep!)

Any help? Are there kernel arguments or something I can add to help it past this problem? Is my method of putting the harddrive in a different machine to install fundamentally unsound? Any suggestion would be most helpful. Thanks.

Please remember: this computer has no CD and no floppy.

---

### Post by philipacamaniac on 2005-05-18
Whereas installing a copy of Windows on one machine and then transferring that drive over to another computer generally works, it doesn't work pretty much at all with Linux.

The problem is, on one computer, your hard disk might be /dev/hda1, but on another, it might be /dev/hdb1 or /dev/hdc1. And that is basically what is happening. I would tell you to use a LiveCD to boot with, and then make corrections to the GRUB configuration, but you have no CD drive.

Fundamentally unsound? I think so.  :)

I'm trying to think of ways that this would be possible. Does it have a network card?

---

### Post by clashxen on 2005-05-18
Thanks for the advice...dang. I got it to run a CLI only version of Slackware (from 1998) using the drive swap method, but it couldn't start the x=server. And i've never tried to setup PCMICIA/networking from the CLI, so i thought I'd try to see if I could get it to work with Ubuntu in the same way, but alas alas....

It has a pcmcia network card (Xircom XEM5600 10/100 & 56k Modem card).

---

### Post by clashxen on 2005-05-18
A quick thought: 
Could I setup something in the grub boot interface to have it look for root on hdb, or hdc? If so, how?

How many choices could it be? Could I just brute force through all the possible combinations until it works? or is this doomed too? Thanks again!

---

