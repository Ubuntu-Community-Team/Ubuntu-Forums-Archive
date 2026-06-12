---
title: "new Suspend issue"
date: 2009-08-15
forum: Hardware
---

### Post by cooltd825 on 2009-08-15
I know, there are a billion and one different troubleshooting tutorials for fixing Suspend/Hibernate issues, but I've tried all I can find and I think I need help on a more personal level now.  

I have a homebuilt PC running an AMD 64 X2 7750 Kuma on an ASUS M3N78-VM motherboard.  My Ubuntu is up to date, running the 2.6.28-14-generic kernel with Jaunty x86_64.  

The computer will hibernate just fine, and it will even suspend no problem, but my problem is resuming from suspend.  It just gives me a black screen on resume, sometimes giving me a mouse.  When I press CTRL+ALT+Backspace I briefly see my desktop background but no icons, toolbars, etc.  Then I get two error messages in the terminal, both identical, saying

[ 2357.174204] end_request : I/O error, dev sda, sector (pick very large random number here)

Is there a configuration file I need to mess with, or is it some ACPI setting in my BIOS?  This problem has only occurred since I updated to Jaunty, with Suspend working just fine in previous Ubuntu releases, along with my other partitions of Windows 7 x64 and Vista x64.  

I can attach anything I need to....

Thanks,
Thomas

---

### Post by nidomedia on 2009-08-18
[ 2357.174204] end_request : I/O error, dev sda, sector (pick very large random number here)

This looks like an error on your harddrive rather then jest suspend. You may want to look at the SMART status and make sure sector 'pick very large random number here' is not part of the resume partition. If it is, that'll explain the error.

you can check out smart using smartctl. there is some gui tool as well, but I forgot the name.

---

### Post by swordphsh on 2009-08-21
This sounds like the same or similar error I'm having. I can't tell exactly because there are about 10 different errors that scroll through the screen, but I did see a few about I/O errors and EXT3-FS errors.

I did, however, look into smartctl and my drive passed the overall-health self-assessment test and does not seem to have any other errors.

---

