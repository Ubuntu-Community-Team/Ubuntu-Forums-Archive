---
title: "2 folders in Sys/Class/Backlight?"
date: 2012-01-11
forum: Hardware
---

### Post by zebrapie on 2012-01-11
**ISSUE:** Backlight brightness does not change. 

**More Detail: **Brightness will not change, using both 'System  Settings->Screen', or FN keys (Brightness bar shows and moves, but  screen brightness does not change). 

Notcied a post in this thread ([http://ubuntuforums.org/showthread.php?t=1866283](http://ubuntuforums.org/showthread.php?t=1866283)) about having multiple folders in Sys->Class->Backlight...
 
 [COLOR=Red]I HAVE TWO FOLDERS TOO![/COLOR]
 
 'intel_backlight' and 'acpi_video0'
 
 Using the function keys, alters the value in the acpi_video0's   'Brightness' file - But doesn't actually alter the brightness of the   screen.
 
 If I add 'backlight=vendor' in Grub, my function keys then edit the   value in the 'Intel_Backlight brightness file. - But again doesnt  actually  change the brightness of the screen. 

**Computer:** Fujitsu Siemans Pi2515, Intel Integrated Graphics, No hdd partition.


**Already Tried:**

-Editing grub to contain: acpi_osi=Linux acpi_backlight=vendor

-http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10

-sudo apt-get install acpi

-$ sudo setpci -s 00:02.0 F4.B=20

-Brightness does not adjust in fallback mode either. :sad:

-Reinstalling OS, Using Linux Mint (Same problem).

-Upgrading and downgrading BIOS.

Many thanks for reading, I understand this problem may need a bit of a  Linux pro to sort. If anyones up for the challenge i'll spend any amount  of time being walked through this, posting results. Don't want to give up here! :smile:

---

### Post by zebrapie on 2012-01-14
Unsure of rules, so apologies if Bumps are not allowed. Still got this problem, any help at all would be great, or any words of advice. Many thanks. Zebrapie.

---

### Post by BlinkinCat on 2012-01-14
No problems with bumps if they are over 24 hour span period - :)

Of course you can respond to answers to your posts at any time.

---

### Post by zebrapie on 2012-01-27
Thank you BlinkinCat :)

Gave up and re-installed Windose, same problem? FFFUUUUUUUUUU Now i'm confused!!

---

