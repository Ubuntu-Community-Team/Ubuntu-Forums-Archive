---
title: "Which is a better way to handle USB Drives?"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by justin whitaker on 2007-02-20
I have a Maxtor USB drive that is my backup drive....it has all my music, my work and personal documents, downloads, etc..

Since moving over to Ubuntu full time, I have moved everything over to Ubuntu, and installed NTFS3...I have not tried to mount and change that drive.

Here is my question: should I format it to ext3 and use it for Linux full time, using the ext3 driver for XP when necessary (which will be infrequent), or leave it as NTFS, and hope that everything works ok when I back things up to the usb drive?

Which is better, in the long run?

And how do I format the USB drive so it is mountable if I decide to convert it to ext3?

---

### Post by madmetal on 2007-02-20
open synaptic and search for gparted, its ok for partitioning and formating.
since you are working your files at both windows and linux i preffer fat32 although its not the best for performance its the safest for dual boot

---

### Post by tgalati4 on 2007-02-20
Linux has a several year history with ext3 and perhaps a few months history with NTFS read/write.

You have answered your own question.  Use ext3 for Linux full time.  Create a small FAT32 partition for Windows to move files between systems if necessary.

For better performance (games for instance) your best bet is to keep a dedicated windows drive formatted for NTFS.  Drives are cheap these days.  No reason not to have both.

Besides, you don't want Windows trashing your shared Linux drive.  Better to keep it separate and locked up.  Windows works better that way.

I have never experienced a blue screen of death when I was not using windows.  That's been my experience.

---

