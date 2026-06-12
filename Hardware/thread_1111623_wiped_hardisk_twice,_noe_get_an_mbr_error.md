---
title: "wiped hardisk twice, noe get an mbr error"
date: 2009-03-30
forum: Hardware
---

### Post by Vincenso Andolini on 2009-03-30
Hello all,

I endeavoured to flatten windows permanently on my computer. This is a process I had completed recently on another computer with no problems. On the computer in question I used Hiren's Boot Cd with Acronis Disk Director and wiped the hardisk twice over. Now when I try to boot from a cd, an Ubuntu cd, the computer (BIOS?) does not allow it and says "MBR ERROR". 

I can press F12 upon startup to access Hirens Boot CD but I cannot boot from an Ubuntu disc. I want to install Ubuntu.  

Does anybody know how I can fix this? I assume that the hardisk has a corruption in the master reboot file (?), but I am new to working with hardisks in this manner so I am not sure what to do.

All help is appreciated.

Vincenso

---

### Post by Therion on 2009-03-30
Let me see if I can explain what might be going on.

You've wiped the only hard disk drive on your computer, so it's now blank (or written over with 1's and 0's or whatever).  So no, you'll not be able to boot from it now but your PC is *trying to* for some reason.

The most likely reason is that the the CD/DVD drive has not been set in the BIOS as a bootable device, or it has not been set as a bootable device *ahead of* the hard drive.

You need to enter your PC's BIOS and find the sequence of bootable devices.  You need to adjust things so that your PC looks to the CD/DVD for something to boot from before going to the hard drive (since we know the hard drive is now blank).  Make sense?

Also, how did you burn this Ubuntu install CD?  Did you burn it as an image file... Meaning a bootable .iso?  Because if you didn't you won't be able to boot from it no matter what.

---

### Post by Vincenso Andolini on 2009-03-30
Thank you for your reply. I checked the BIOS already, CD booting is set as #1 boot order, and it is ahead (of course) of the HDD.

I did burn the Ubuntu as an .iso, this cd has already been successfully used to boot from cd and install Ubuntu.

What else might it be?

Vincenso

---

