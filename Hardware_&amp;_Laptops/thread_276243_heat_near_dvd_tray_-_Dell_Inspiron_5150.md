---
title: "heat near dvd tray - Dell Inspiron 5150"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by lone_marauder on 2006-10-12
I noticed that when I ran Ubuntu 6.06 on my Dell 5150 laptop, the system seemed a little warm to the touch on the left side - around where the DVD drive is.  I don't notice this problem in Windows, and I don't notice this problem if I run Gentoo on the laptop.

Thinking it might be something related to the drive, I worked with the drive open for a while to see if some sort of automount were responsible for the excessive heat.  This had no effect.  The only other component in this general area is the southbridge chip.

I decided to quantify it just to make sure I wasn't imagining things.  I inserted a thermocouple into the DVD drive and closed the door.  I ran for an hour in Ubuntu 6.06 and an hour in Windows.  I noted the temperature at the end of each run:

Ubuntu -   47.2 C

Windows -  36.9 C

I am using i8kfangui and i8kmon to control the CPU fan.  I am using the same temps for both programs.  The processor actually seems to run a few degrees cooler in Ubuntu.  

What's going on here?

---

### Post by lone_marauder on 2006-10-16
I have determined that the module ide_cd is causing the problem.  If I unload this module, the temperature will drop back to a reasonable level.  Obviously, this problem is related to the CD rom drive.  No idea why ejecting the tray didn't help.

---

