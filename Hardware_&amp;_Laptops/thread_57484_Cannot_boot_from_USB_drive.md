---
title: "Cannot boot from USB drive"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by LodeRunner on 2005-08-16
This isn't strictly Ubuntu related, though it does install Grub by default and part of my question is Grub-related.

First, I should admit that it seems as though I don't know a damn thing about MBRs.  I thought I had a vague (but useful) notion of how they worked, but recent experiences have me baffled, and googling has yet to yield any useful info.

What I have done so far:

Dell Inspiron 6000D; have Ubuntu installed on the internal hard drive.  On another computer, I installed Windows XP on a 3.5" hard drive, stuck it in a USB 2.0 enclosure, tested it to ensure that my laptop recognized the drive (it did, and Ubuntu auto-mounted it), and then I tried to boot from it.  Hitting F12 ("Boot Menu") and selecting USB drive took me to Grub (which has only Ubuntu listed.) I went into the bios and set the USB drive to the #1 boot priority and again, it went straight to Grub.  

This had me completely stumped.  I pondered for a bit, then turned on the desktop I had used to install XP on the hard drive.  Instead of booting Windows normally, it took me to a screen to select which install of Windows XP I wanted to use (only one of which was functional, because the other drive was in my enclosure and thus not in the desktop anymore.)  I guessed that the XP installer, in its infinite wisdom, decided not to bother making an MBR for the second drive and thus it was only bootable via the MBR of the first drive.

So I booted the XP install CD on the laptop, wiped the external HD, and tried to reinstall windows on it.  It tells me that it must write some startup files to the following disk: blah MB Disk 0 at ID 0 on bus 0 on atapi [MBR].  This is my internal HD.  The external is simply referred to as "blah MB disk [MBR]".  It says that it does not see any XP-compatible partitions (which is odd because the previous screen recognized one of them as FAT), so it innocently suggests that I delete an existing one and create my own (seemed like a really bad idea, so I didn't.)  

This is where my confusion and lack of knowledge comes into play.  I thought that I could install Windows on one HD and Ubuntu on the other and not worry about partitions and MBRs and bootloaders and stuff.  To switch OSes, I would simply use the F12 Boot Menu (or failing that, change the boot order in the bios.)  I don't understand why I can't have 2 MBRs and tell the bios which one to use every time I boot.  If the internal drive wasn't there, XP would (in theory) install just fine, so why does it HAVE to install stuff on it?  That makes no damn sense.  There's no option in the bios to specify a primary drive or MBR, so why would it just assume that I want all my OSes to be bootable through a single disk  (especially when I already have a handy dandy bios-based quick Boot Menu?)

Anyway, my confusion aside, I guess the only way to do this now is through Grub.  How do I add Windows XP to the menu?  Am I going to have to use the desktop again to reinstall Windows, or is there some way of letting Windows write its startup files and then having Grub fix it so I can dual boot?

I still think I'm missing something here.  I thought the entire point of boot from USB is that you can plug your drive into any compatible computer and boot your OS of choice without touching that computer's internal hard drives... right?  I mean hell, the XP installer can boot from the CD just fine and it hasn't messed around with the internal HD's MBR or Grub.  Knoppix and the Live CD craze itself is centered around this very fact.  It shouldn't be any different when it comes to hard drives.

In short, I have a problem and I am very confused.  I would like a solution and enlightenment, but at this point I will settle for merely the former.

---

### Post by kimo123be on 2008-01-23
did u try boot loaders !!!

---

