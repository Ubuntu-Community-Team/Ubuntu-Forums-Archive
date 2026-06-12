---
title: "How do I quickly restore default video driver when proprietary driver fails"
date: 2013-07-12
forum: Hardware
---

### Post by CrankyOldMan on 2013-07-12
I suppose this question has been asked a thousand times, but I performed a search and could find no postings. 

I have a desktop with a Gigabyte GA-EP45-UD3P motherboard and a 9800GT-500 video card.   Last spring, when I installed 12.04LTS, the machine selected a default video driver which does not support the 3D features of Unity.   I tried one of the proprietary drivers, and restarted, as requested.  The machine booted up, but the desktop was all screwed up.   I couldn't reach the unity bar and system settings to revert to the original driver.  I actually had to reinstall 12.04 to get a viewable desktop.

There must be a SIMPLE way to revert to a previous driver before the machine loads the desktop.   How?

---

### Post by jp734 on 2013-07-12
If you have xorg.conf file, make two copies of it. One with proprietary driver and one with VESA. When your pc wont boot using the proprietary driver, simply copy the one using VESA to /etc/X11 as root and it should work

---

