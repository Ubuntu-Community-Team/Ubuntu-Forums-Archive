---
title: "Lexar JD Touchguard (Hoary)"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by oracle on 2004-12-26
Good morning all!

I've sifted through these forums and Google trying to find the answer to a few questions that came about after I received a Lexar Touchdrive for Christmas.

First, I had some trouble getting Ubuntu to mount the drive.  I checked the dmesg and it not only saw that I had plugged something in to it but also identified what it was.  The issue is that it would not mount it.  After some searching I found that I needed to add a line to my fstab which now will mount the USB drive but then when I try to unmount it I get "could not run pumount, permission denied."  When trying to run the command manually with sudo I get a new error stating "device must exist in /dev".  Any ideas on that one?  I'm sure I forgot something small.

Second question.  Any software that will run the on board thumbprint scanner, or do I have to use WINE and the program that came with it?

Thanks!!

Phil

---

