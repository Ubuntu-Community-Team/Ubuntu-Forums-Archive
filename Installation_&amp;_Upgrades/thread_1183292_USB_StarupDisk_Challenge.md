---
title: "USB StarupDisk Challenge"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by loudog23 on 2009-06-09
Hi everyone, I have two challenge for you:

NUmber 1
USB device: BenqJoybee130 (256mb internal + 1gig sdCard)
I managed to put a live cd on the sdcard.

Q: Now, is there a way to grub the 256mb so i can boot from it 
and then load the live cd on the card?

Issue #1: 256mb in not enough for the startupdisk, 
i know it is enough for a /boot partiton tho

Issues #2: On my personal system i can boot from the card directly, but some system do not detect the card at boot time. Only the 256mb is detected as a boot drive.

NUmber 2
USB Device: External HDD

Q: Is there a way to have multiple image on 1 disk and make it so you can grub the one you want

Utility: To be able to boot a live session on many different platform (i386, amd, mac) from the same disk.

Any input would be appreciated.
Have a good one
lou

[SIZE="1"]can someone tell how to make a MAC boot on usb device?[/SIZE]

---

### Post by Mighty_Joe on 2009-06-10
> **loudog23 said:**
> 
NUmber 2
USB Device: External HDD

Q: Is there a way to have multiple image on 1 disk and make it so you can grub the one you want


The easy way would be to create different partitions for each distribution and just install it (as opposed to using the Live CD image).  You can configure Grub to have a menu entry for each partition/distribution the same one sets up dual/multiple boots(this is speculation on my part, never done it).
I don't know if it can be done with multiple Live CD images.

> **loudog23 said:**
> 
[SIZE="1"]can someone tell how to make a MAC boot on usb device?[/SIZE]

The [Mac FAQ ]("http://ubuntuforums.org/showthread.php?t=1046568")says it can't be done (though there are exceptions).

---

