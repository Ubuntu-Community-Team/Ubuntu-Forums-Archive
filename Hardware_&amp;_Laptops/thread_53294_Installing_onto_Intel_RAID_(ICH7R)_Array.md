---
title: "Installing onto Intel RAID (ICH7R) Array?"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by Jeff250 on 2005-07-31
I've got an Intel SATA RAID 0 array (via an ICH5R southbridge) with already a Windows partition plus 36GB of unpartitioned space that I'd like to use toward Ubuntu.  I tried using the Ubuntu setup CD to install it, but the setup seemed to detect the drives in the array seperately instead of as a part of an array and didn't seem able to detect the NTFS partition already present either (much unlike its succuss with my IDE drive).

Now, of course, this comes as absolutely no surprise, because, when installing Windows, I've had to always give the setup my Intel RAID drivers via floppy disk (or, as I soon learned to do, via my own "tweaked" installation CD) so that the setup program could use the array.

Anyone know if I can install Ubuntu onto the array?[IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG]

edit:

Fedora Core 5 is supposed to have support for BIOS RAID, including installing onto it.  However, the only current Ubuntu solution for BIOS RAID is to just not use it and use Ubuntu's RAID instead.  This is fine, except for dual-booting with Windows.

A completely hardware RAID solution (e.g. by an expensive PCI card) should work with both Windows and Linux and look just like another drive to the setup.

---

### Post by kosmic on 2005-07-31
This is just my 0.02 cents ;)

But try to partition that drive in Windows with a program like Partition Magic, and format the 36 GB you have free with a ext3 our ReiserFs format, then boot the Ubuntu Install CD and I hope you can see the 36GB space avaible...

---

### Post by JuanPedro on 2005-08-07
it dowsn't work

---

### Post by Jaxor on 2005-08-18
I am in a predicament very much similar to Jeff250.

I am also quite "tech savvy" but new to Linux. My sata raid (stripped) comes with a driver that can be installed via floppy. Normally, like Jeff250, I don't have to worry about the driver, because I slipped it into a tweaked windows install cd. With Linux, it cannot find the raid at all, and hangs at the install. I've verified this problem by successfully installing Linux when taken out of raid.

Is there any way to slipstream this driver into a Linux install package so it can install/boot off of the sata raid? Or is there a different/better way?

Any help would be greatly appreciated. :)

---

