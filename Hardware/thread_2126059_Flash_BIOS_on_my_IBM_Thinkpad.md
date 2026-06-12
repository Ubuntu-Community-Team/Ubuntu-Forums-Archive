---
title: "Flash BIOS on my IBM Thinkpad"
date: 2013-03-15
forum: Hardware
---

### Post by coreybell on 2013-03-15
I need help flashing my BIOS on my IBM ThinkPad 1858 W19 R52. I got this laptop from a friend of mine, and instead of using the original hard drive that came with the IBM Thinkpad, I took my hard drive out of my other laptop and replaced it in the thinkpad. The thinkpad boots up fine, it just gives me this error message when it boots 

[B]"2010: Warning: your internal hard disk drive (HDD) may not function correctly on this system. Ensure that your HDD is supported on this system and that the latest HDD firmware is installed."

When this pops up I have to press ESC to continue booting or I can press F1 to enter setup menu.

[/B]Once I press escape, my Thinkpad continues the booting process and everything works fine. It is really not a problem just a little adjutating that's all. [B]

Can someone help me I JUST WANT TO FLASH MY BIOS.


[/B]

---

### Post by williejones on 2013-03-15
What makes you thing a BIOS flash will help?  Lood at the message at starting up.

> **Ensure that your HDD is supported on this system and that the latest HDD firmware is installed.**

---

### Post by tgalati4 on 2013-03-15
That message is hard-coded in the BIOS whenever you install a non-IBM disk drive.  It's a pain, but I don't reboot often, just put the machine to sleep.  I don't think a BIOS upgrade will fix that.  The message is a reminder that a non-IBM disk drive may not have shock protection or security-wipe, or encryption, or support from IBM.  But the drive will work, regardless.

If you really want to flash the BIOS, you can burn a CD with freedos and your flash code on it.  Or you can add freedos to your /boot directory and add a grub entry.  Put the flash ROM image into /boot along with the *.exe installer.  When booted in freedos, just run the installer.  That's how I did mine.  I found a tutorial, but I don't have the link handy.

How about this:  [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by linrunner on 2013-03-17
Hi,

you may try this BIOS: [ISO]("http://dl.dropbox.com/u/15415342/no2010/R52_76ET69WW_SLIC2.1_no_1802_no_2010.iso") ([Source]("http://thinkpad-forum.de/threads/124788-no_1802_no_2010-BIOS-Sammlung")).

Before you flash please check:
- Is your BIOS the latest Lenovo-BIOS? If not, update BIOS and EC firmware
- Do you really have a R52 systemboard inside? Enter BIOS to check

**Disclaimer: if you brick your ThinkPad with this, don't complain to me!**

---

