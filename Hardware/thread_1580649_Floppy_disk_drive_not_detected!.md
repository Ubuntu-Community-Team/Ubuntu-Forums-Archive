---
title: "Floppy disk drive not detected!"
date: 2010-09-23
forum: Hardware
---

### Post by BD338 on 2010-09-23
Hi there!
I had left my desktop alone (turned off) for like 6 weeks, before I decided, that I wanted to use it again. I decided that I would like to install Windows on it, so that I had a computer running MacOSX,  one running Ubuntu, and one running Windows. - And so I did. The only problem is that once I booted up in Windows, there was no floppy disk drive. I found out so by opening "Computer" from the start menu, but it only showed my hard drive and my CD/DVD drive. Typing "a:" in the command prompt resulted in: "Windows could not find the drive specified.".
I tried taking out the drive, and actually disassembling the entire computer and assembling it again, nothing helped. So I decided to re-install Windows... didn't help. I also tried swapping the old floppy drive with a new floppy disk drive, no luck.
So I finally decided that it was Windows' fault, and decided to install Ubuntu (both 7.10 and 10.10) on the computer, but my floppy disk drive doesn't show up in here neither... in Ubuntu's 'Device Manager' the only floppy disk related thing that I am able to find is a floppy disk controller (just like in Windows)... also, there is no fd0 or anything in my /dev folder.
I really hope that someone might be able to figure it out. I also might throw together a quick program to see if the BIOS is able to communicate with the disk drive, BEFORE any type of OS is loaded (if so I'll keep you updated), as I am beginning to suspect the motherboard to be the mother (pun intended) of this problem.
Either way, I really hope that someone knows what I'm supposed to do! :)

Best regards,
Benjamin.

---

### Post by pricetech on 2010-09-23
I'd start by resetting the BIOS to defaults.  It may be that the drive is turned off somewhere, maybe more than one place.

---

### Post by BD338 on 2010-09-24
> **pricetech said:**
> I'd start by resetting the BIOS to defaults.  It may be that the drive is turned off somewhere, maybe more than one place.
I'll try that ;).

---

### Post by BD338 on 2010-09-24
It worked! Thanks a bunch!! :)

---

