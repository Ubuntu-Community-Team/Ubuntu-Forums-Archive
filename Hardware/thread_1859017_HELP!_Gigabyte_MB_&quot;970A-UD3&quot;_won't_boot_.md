---
title: "HELP! Gigabyte M/B &quot;970A-UD3&quot; won't boot from USB"
date: 2011-10-13
forum: Hardware
---

### Post by UserDemos on 2011-10-13
Hey there fellow members,

I just recently built myself a desktop with a Gigabyte "970A-UD3" motherboard and installed Ubuntu 11.04 with a friends CD-ROM because I don't have my own yet. 

I'm looking to do a fresh install from USB stick of the new Ubuntu 11.10. I used the startup disk creator and made one, but alas CANNOT get it to boot. I've tried F12 and manually selecting all the options but it boots straight to my OS. I see that it's accessing the drive and then it goes into the OS boot, no USB boot as selected. Tried changing orders in the BIOS, etc. Nothing. I even made the installation again on the USB drive, still nothing. 

Anyone have any thoughts or ideas? Am I just doing something incorrectly. Maybe I am missing a simple step? Any help would be gladly appreciated.

Thanks tons in advance!

---

### Post by sglow on 2011-11-08
I've got the same motherboard and the same problem.  Did you ever get this working?

---

### Post by HsH on 2011-11-30
I have GA-970A-D3 motherboard.

With "Transcend" flash (2Gb, 16Gb) PC don't boot, but with "Kingston" 2Gb boot fine. At the others PC "Transcend" flash boot normally.

The same problem with any Linux distribution, and even with the Windows7 on flash, so I think that trouble is hardware issue.

---

### Post by armanbf on 2011-12-08
[solved]
I had the same problem. I 'installed' ubuntu on the usb first and it worked like charm. 
ubuntu live usb partition table is 32bit (fat?) so the amd64 bit systems can't boot from it..

---

### Post by HsH on 2011-12-12
> **armanbf said:**
> [solved]
ubuntu live usb partition table is 32bit (fat?) so the amd64 bit systems can't boot from it..

In that case filesystem type on a boot media does not matter.
Win7 can boot only from ntfs, also
> At the others PC "Transcend" flash boot normally.

---

### Post by Klau3 on 2011-12-14
Same problem here.
We can't boot from CD or USB  regardless of our BIOS settings :(

---

### Post by dandnsmith on 2011-12-14
> **UserDemos said:**
> Hey there fellow members,

I just recently built myself a desktop with a Gigabyte "970A-UD3" motherboard and installed Ubuntu 11.04 with a friends CD-ROM because I don't have my own yet. 

I'm looking to do a fresh install from USB stick of the new Ubuntu 11.10. I used the startup disk creator and made one, but alas CANNOT get it to boot. I've tried F12 and manually selecting all the options but it boots straight to my OS. I see that it's accessing the drive and then it goes into the OS boot, no USB boot as selected. Tried changing orders in the BIOS, etc. Nothing. I even made the installation again on the USB drive, still nothing. 

Anyone have any thoughts or ideas? Am I just doing something incorrectly. Maybe I am missing a simple step? Any help would be gladly appreciated.

Thanks tons in advance!

If you did that install from friend's CD drive, how was it attached to your system - or did you do the install with your HDD on the friend's PC?

There's confusing crud in this thread, from users who don't seem to have exactly the same situation.
These users should either start their own threads, or just watch to see if this instance can be sorted out!

---

### Post by zitstif on 2011-12-26
I have the same exact issue with this motherboard. I even had issues booting from my SATA DVD-RW drive. 

At the time (around Halloween this year) updating to the BIOS version F3 seemed to solve the issue of problematic booting off of my SATA DVD-RW drive. 

Now that x-mas has come around and that I have a microsd card that I would like to install linux onto via a usb flash drive, I am not able to boot up off of any usb device. 

If I get ambitious I might try doing an update to my bios to version F5b. (Though it is Beta..)

[http://www.gigabyte.com/products/product-page.aspx?pid=3907#bios](http://www.gigabyte.com/products/product-page.aspx?pid=3907#bios)

If anyone else wants to give this a shot before I do, that would be great. :-)

---

### Post by zitstif on 2012-01-03
To save others time and energy:

I have tried the F4 BIOS for this motherboard and it still wouldn't boot off of any of my bootable flash drives. 

I have tried using the F5b BIOS and it was horrible! It was very glitchy and I would advise anyone else to not use it! 

This is very frustrating for me because there is something I would like to work on that requires me booting off of a USB flash drive. ](*,)

---

### Post by Mark Phelps on 2012-01-03
I would agree in not rushing into upgrading the BIOS on the Gigabyte board.  I used to use ASUS boards and always upgraded to the latest BIOS, even the Beta versions, and never had a problem.

Then, I bought a Gigabyte and a few weeks later, noticed that the BIOS was really out of date. So, I (mistakenly) upgraded to the latest BIOS.

THEN, not only would my 1600 memory no longer boot at that speed, it wouldn't even boot at 1333. I had to slow it down to 1033!

Fortunately, I had saved off the "old" BIOS,so I reflashed using that, and was back to being able to use my memory at full speed.

---

### Post by dirkbecker31 on 2012-01-06
I had the same problem with my GA-970A-D3 motherboard. It was not possible to boot from USB (stick or USB card). 
I found out that the reason for this behaviour is the formatting of the USB medium. 
I tried many formatting tools but only the "HP USB Disk Sorage Format Tool" succeeded. 
So my way to get a bootable Ubuntu USB medium for my GA-970A-D3 motherboard is 
1. Format the USB medium with "HP USB Disk Sorage Format Tool"
2. Use "Startup Disk Creator" or "UNetbootin" to get it bootable with an Ubuntu distribution.

---

### Post by zitstif on 2012-01-06
"1. Format the USB medium with "HP USB Disk Sorage Format Tool"
2. Use "Startup Disk Creator" or "UNetbootin" to get it bootable with an Ubuntu distribution. "

This is fine and dandy for those who want to do live-usb booting but I need to do a permanent install on a micro-sd card where the sd card will be formatted.

End users shouldn't have to use a specific tool for formatting their USB drives. This is definitely an issue with the motherboard firmware. Gigabyte needs to address this issue.


But thank you for your words of wisdom dirkbecker31. :-)

---

### Post by dirkbecker31 on 2012-01-07
> This is fine and dandy for those who want to do live-usb booting but I  need to do a permanent install on a micro-sd card where the sd card will  be formatted.The only way in this case is to format the SD card with FAT32 (with "HP USB Disk Sorage Format Tool") and then to install Ubuntu without formatting. 
I know this is not nice...:(

---

### Post by deeplodokus on 2012-01-28
Hi people.
Finding myself having the same issue... My thumbdrive is a first-price thumbdrive, but it boots fine with just any other computer. This is the first time I'm having a computer that refuses to boot from USB and I'm tempted to say that if it comes from the mobo, then I'll never go for Gigabyte again.
Anyway, just upgraded BIOS from f1 to f4, but as said by other people previously, it didn't help.
I'm GRRRBMLDM!
If you guys have a solution... I'm all ears!
Thanks!

---

### Post by Rolo linux on 2012-05-03
Hi,

I have this motherboard, and the only way to boot from the flash drive is to install the iso of ubuntu from Windows with a program like "USB Universal Installer" or "LinuxLIVE USB Creator". I managed to boot from USB and do the installation, but when rebooting the first appears classic screen purple and then turns pink and there is, can not start Ubuntu 12.04
The live usb works fine. For now I'm using Windows in this machine and I hope the next release of Ubuntu solve the problem. I think the issue is relative to the graphics card: Gigabyte  6670.

Rolo

---

### Post by HsH on 2013-02-21
My solution - use [**plop boot manager**]("http://www.plop.at/en/bootmanagers.html") launched from GRUB. It works fine with all USB flash drives.

---

### Post by codemaniac on 2013-02-21
Old thread closed.

---

