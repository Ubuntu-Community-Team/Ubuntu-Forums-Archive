---
title: "Initramfs: could not mount /root partition: device busy o_O"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by athorretto on 2009-03-22
hi all,

on this system i had working 8.04 ubuntu studio with no problems.
i decide an update , in an emptyed serial ata disk and at boot i'm in the initramfs prompt because the system can't mount the root partition: 
ex mount /dev/disk/by-uuid/<my disk> fails with device busy error.

I've already checked that the uiid is the correnspondig id of the device where ubuntu studio is.

checked grub parameters such path of the image ecc...

all seems right but he didn't start :( i had always with the error device busy during /root mounting.

Tried also to refeer disks by path/label didn't work

that could be serial ata problem?

---

### Post by kennethmsmith on 2009-04-14
Can't help you (yet), but maybe you can help me if you have solved your issue.  I run into the same kind of error message "could not mount /dev/disk/by uuid..." after a wubi install of ubuntu.  Tells me to try chkdsk on my windows drive and then restart into windows, and then restart into linux, but that didn't work.  I don't get it.  The install appeared to go fine, but now i can't get into ubuntu at all.

please help if you can.

UPDATE:  I downloaded the official 9.04 version and made a live CD and went into windows and did a wubi install.  now everything seems to be working.. not sure what caused this before.

---

