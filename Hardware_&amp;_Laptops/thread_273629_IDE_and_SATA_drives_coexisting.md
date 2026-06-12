---
title: "IDE and SATA drives coexisting?"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by MikeBenza on 2006-10-08
I have a Dapper machine with a mobo that supports IDE and SATA.  There are no SATA drives in it, only IDE, but there are two SATA drives in the mail.  Can I add the SATA drives, or must I choose one or the other?

Since /dev/hda and hdb are taken, will the two new ones be hdc and hdd? 

- Mike

---

### Post by colo on 2006-10-08
Serial ATA Devices, like everything else SCSI-like, is to be found under /dev/sd*. It's no problem to operate PATA and SATA at one time with the Linux kernel. There could, however, be problems with your BIOS and the Bootloader (GRUB), which relies heavily on the order of how your BIOS propagates your drives to other programs on your PC - but that's fixable and should not bother you until you actually have to deal with it.

---

