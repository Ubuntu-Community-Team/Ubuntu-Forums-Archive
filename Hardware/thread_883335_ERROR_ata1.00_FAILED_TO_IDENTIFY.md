---
title: "ERROR: ata1.00 FAILED TO IDENTIFY"
date: 2008-08-07
forum: Hardware
---

### Post by mortalic on 2008-08-07
Ok all you hardware uber geeks, I am stuck and need your help.

I recently wiped 7.04 and installed 8.04 on my storage/printer server.  The install failed trying to boot the live CD, drops me out to busybox with the following error over and over again:
ata1.00 FAILED TO IDENTIFY (I/O ERROR. ERR_MASK=0X4)
failed to recover some devices
unable to find a medium containing a live file system

After a fair amount of searches I found out that the Dell Vostro's suffer from this same issue and there are two workarounds.  You can change your Bios Sata type to RAID (even if you don't have a raid) or you can add all_generic_ide to the grub menu.lst file.  The bios option did not appear to work (I don't have a dell, it's an asus A8V-MX motherboard) so I added the line to grub.  This got me through the install and everything.  I started to copy all my data from one sata drive to the other (about 320ish GB) and it is telling me that I will need to wait 44hours!!!!!!  Obviously there is a performance hit when you use the all_generic_ide option.

Can someone possibly explain how to actually fix this issue?  the way I see it, I can research this for 2 days and if we can figure it out I'll still come out ahead!

Thanks!  Let me know what other information I can post!

---

### Post by mc4man on 2008-08-07
I've never had any issues with drives ect. so if this is a dumb response I do apologize. Now that you have 8.04 installed have you tried removing the all-generic parameter and booting up normal?


edit: what I imagine might happen is you'll boot up fine, the sata hdd drives will work fine and your dvd drive (which I'm assuming is a sata drive) won't be detected. If that's the case there _may_ be a workaround other than the all-generic.... which is clearly unsuitable.

---

### Post by mortalic on 2008-08-08
Well unfortunately that's not exactly the issue.  The CD drive is an IDE drive, the HDD's are both SATA.  I have removed the all_generic_ide option and tried the three modes in  my bios (SATA, RAID, AHCI) on 8.04 but it still drops out to busybox with the error.  So I had to add the all_generic_ide line back to grub.

LOL on the plus side I've transfered a whopping 32.1gb since my first post. LOL.. *sigh*

---

### Post by mortalic on 2008-08-08
Bump, does anyone have any help?  This is really something I don't know how to fix.

---

### Post by mortalic on 2008-08-09
Ok, I managed to find out how to fix this, and not lose performance such as when you add all_generic_ide.

This works on the Asus A8V-MX motherboard, I have bios revision 503, change your chipset's southbridge mode to AHCI, modify your menu.lst file that has the main kernel line, and add:
pci=nomsi 

I found that on this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454)

from this poster:
btherio

good job btherio!

---

