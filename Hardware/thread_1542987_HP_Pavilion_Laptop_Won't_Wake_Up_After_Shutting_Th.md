---
title: "HP Pavilion Laptop Won't Wake Up After Shutting The Screen"
date: 2010-07-31
forum: Hardware
---

### Post by kajiotaku on 2010-07-31
The model is HP Pavilion DV7 something rather, running Ubuntu 10.04 (Not Netbook Edition (Yes it can handle it)).  At first when I closed my laptop, it would go to sleep fine and wake up and display the password prompt a couple seconds after I open it.  About a month later and I close it, open it up, and it takes about a minute for the password prompt to appear or it takes so long that I grow tired of waiting and hold the power button down because a reboot would be faster.  Last update: A few minutes ago.

How do I fix this?

---

### Post by kajiotaku on 2010-07-31
Bump.

---

### Post by lidex on 2010-07-31
Look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/7#suspend)

---

### Post by kajiotaku on 2010-08-01
[ftp://ftp.hp.com/pub/softpaq/sp43501-44000/sp43550.exe](ftp://ftp.hp.com/pub/softpaq/sp43501-44000/sp43550.exe) doesn't exist.  I'll try to find the file on other websites though.

---

### Post by kajiotaku on 2010-08-01
Will the newest .exe in [ftp://ftp.hp.com/pub/softpaq/sp43501-44000/](ftp://ftp.hp.com/pub/softpaq/sp43501-44000/) work for my laptop?

---

### Post by Tsingtao on 2010-11-15
Just re-installed 10.10 64 bit in my HP dv7-4053 laptop.  Could not wake it up a after closing and opening the screen.  It had not been a problem in my previous 10.04 installation.

Did a search and found many posts on possible fixes.  Several of them mentioned the video driver.  A lightbulb went off in my head.  This tiime I installed the proprietary ATI/AMD FGLRX driver; I didn't recall doing that last time.

Removed the driver and now I have no problem with the computer waking up.

---

