---
title: "Error reading boot CD"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by rainyday_smile on 2009-09-19
I'm completely new to all of this, so please bear with me if something doesn't make much sense!

I successfully downloaded ubuntu and burned it to a CD and changed my bios boot sequence to boot from CD.

I put the CD into my DVD ROM and rebooted my computer, only to have it load up with Windows over and over. So I tried putting the CD into my DVD R/RW and lo and behold, it loaded up ubuntu. I put in my language and tried to 'try ubuntu without any change to your computer' but got hit with an error message. The error message said: "error reading boot CD" and gave me the option to reboot. I rebooted and tried to install instead but got hit with the same error message again.

Can anybody help me out with what this means and what I need to do to fix it please?

---

### Post by stlsaint on 2009-09-19
use a cd-r instead of cd-rw for booting into internal cd/rom...that was a fix for a previous issue encountered. also when you burn the iso make sure you burn it as slowest speed possible (try 4x)

---

### Post by Partyboi2 on 2009-09-19
Also check that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches for the Ubuntu iso that you downloaded before burning it to a disk.
Once you know that the download ubuntu iso  md5sum's is good burn it to a disk, as stated by stlsaint.  Then once you have booted the live cd choose the option at the Main Menu to check the cd for defects.

---

