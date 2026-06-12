---
title: "booting from a usb cd drive, when laptop does not support usb booting!!!!"
date: 2008-08-29
forum: Hardware
---

### Post by mooglinux on 2008-08-29
Here is my dilemma: i have an old Dell latitude L400. this has no floppy disk, no cd drive, and bios does not support bootable usb devices. I did a network install of ubuntu (installing ubuntu without cd drive or floppy drive, only windows 2000, is...an interesting experiance lol) and have that working, but i really want to put gOS or some other operating system on there that is lighter weight. I dont like being chained to what seems to be the only distro with a netboot installer. 

So i want some way to add an entry to grub to boot from my external usb drive. ive read that grub does not support usb devices, so is there some other way to get around this? some kernel i can boot that will in turn let me boot from the cd drive? I know this is far from the only notebook without a cd or floppy disk, so surely someone out there has found a solution to this dilemma?

thanks in advance!

---

### Post by nicedude on 2008-08-29
Grub supports booting form USB sticks, tons of people do it with Linux. I don't like using them that way though but it works. What matters is if your PC supports booting from USB in its BIOS, usually it will have boot from USB hard drive etc. But if your PC is really old it may not have such settings but then again it may so you will have to look. If it does try googling booting Ubuntu from USB and see if you don't find a bunch of guides etc on exactly how to do it. Basically though if your BIOS support it then the USB becomes like any other hard drive to Grub.

Hope that helps, and Goodluck

---

### Post by mooglinux on 2008-08-29
the problem is that the bios DOES NOT support booting from usb. im thinking along the lines of a grub entry that points to a usb device, preferably in this case a cd drive. this is the grub already installed on the hard disk, i know that grub can be put on cds and usb drives, but booting to that is the real challange.

---

### Post by mooglinux on 2008-08-31
looking about i have coem accross something called the PLoP boot manager, and this looks promising, but again with the installing without cd or floppy. Any suggestions on how i could install that?

---

### Post by EscapePod on 2008-09-07
I am able to boot my L400 from USB (external) devices.  I have BIOS revision A09.   If you have a BIOS revision lower than that, you might check the Dell support site to see if you can download a newer version.  Unfortunately, you will still need some way to update your BIOS with the new version.  I was fortunate in that someone in our company had the floppy drive for the L400.

---

