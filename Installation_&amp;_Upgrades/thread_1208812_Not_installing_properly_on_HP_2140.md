---
title: "Not installing properly on HP 2140"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by aremat on 2009-07-09
Hi,
I am absolutely new to ubuntu, but followed a link on the internet to set up my new HP 2140 with dual boot.  First I downloaded the ubuntu 9.04 files.  Then I made my usb stick bootable.  It is booting up and I am (was) able to start ubuntu 9.04 from the stick.
Then I tried to install in on the hard drive (I'd already made a new ntfs partition 15 GB large.
However, the installation starts, but only a bunch of text lines run over the screen and then the text remains on the screen and nothing more happens.
 
At the bottom of the long text lines I see the text End trace dclef0fdd9b2ec04 and "Unknown boot".  One time I also saw the text "Bug: Unable to handle kernel.
 
Does anyone have experience with installing dual boot on this machine and have anyone seen this error (probably yes).
 
Hoping for some help.
 
Regards
Are
Norway

---

### Post by tdowlingjr on 2009-07-09
i am having the same issue.  i am trying to install it on a 16GB SD card.  I have tried installing with the USB Key with the remix version.  I also tried installing the standard version from CD.  Both are giving me the same error msgs as you are getting.
 
Any help would be great.

---

### Post by NastyNative on 2009-07-09
Well 1st of all ubuntu does not recognize ntfs partition.

Are u both already running windows?

or is this a clean install into its own hard drive?

---

### Post by Mark Phelps on 2009-07-10
Ubuntu can't install to an NTFS or FAT32 partition -- the latter is generally the default filesystem used to format flash cards.

You have to create an Ext3 or Ext4 partition to use to install Ubuntu, or just leave some space unallocated and let the installer do the formatting.

---

### Post by tdowlingjr on 2009-07-10
I have windows XP Home on the 160GB HDD.  It came with it on the 2140.  I want to install UNR on a 16GB SD card that I just both.  But it doesn't get to that part yet.  I boot up with the USB key with UNR or CD using the standard edition, I enter in English as the language, then it abends after that.
 
I need windows to do my job, but it is slow when coming up.  I wanted to have UNR installed on the 16GB SD card so I can boot up quick, check email, surf the web, then if i have to do my job, i can reboot the machine to XP on the 160GB drive.
 
Can I do it?  thanks in advance, TJ

---

### Post by tdowlingjr on 2009-07-13
Ok, using the instruction from:  [http://nickcharlton.net/post/ubuntu-on-sdcard/](http://nickcharlton.net/post/ubuntu-on-sdcard/)
 
I booted up the 2140 using the UNR 2GB USB key.  Instead of doing the the install, I ran the live CD and then clicked on the 'install' icon and installed UNR on my Kingston SD4/16GB SDHC card.  When I rebooted the 2140, i hit f9 to go to the SDHC card.  It went into GRUB, then it abended again with the same info as before.
 
Is anyone else having issues?  I have updated the bios to the lastest F03.  Any other idea?  
 
Thanks in advance. TJ

---

### Post by tdowlingjr on 2009-07-13
Ok, after doing some more testing, I think i got it. With not touching the factory install of XP on the 160GB drive, I wanted to install the Remix version on a 16GB SD card.  Here is what I did.
1) Install Remix version on USB key (.IMG file)
2) boot from USB and do not install, go into live mode.
3) once in live mode, click on 'install' icon and install remix on the 16GB SD Card
4) once installed on SD card, reboot machine and hit F10, go in and 'disable' dual-core
5) save settings and reboot, hit F9 and boot from SD card.  It works great!!

---

### Post by doubletop on 2009-07-25
I'm having the same problem with 9.04 on a completely clean HP2140 that only has (had) freeDOS installed on the 80Gb SSD. 8.10 installs fine with no issues. Even the version of 9.04 that runs from the CD fails with the same error.

I also had the same problem after the reboot when I did an upgrade from 8.10 to 9.04, in update manager. And I have just found the same error occurs when I do the 'check disk for defects' in the install menu. (is it trying to check the CD or the hard disk?)

The main error seems to be

[  3.219115] [<c07373a4>] ? unknown boot option+0x0/0x1f8

Any clues if there's a log file somewhere and I'll post it

---

### Post by doubletop on 2009-07-25
Its a known problem with the fix here 

[http://bugs.launchpad.net/ubuntu/+so...ux/+bug/376728](http://bugs.launchpad.net/ubuntu/+so...ux/+bug/376728)

Disable Dual Core in the BIOS

Also the best thread for the 2140 is here

[http://ubuntuforums.org/showthread.php?t=1088743](http://ubuntuforums.org/showthread.php?t=1088743)

---

