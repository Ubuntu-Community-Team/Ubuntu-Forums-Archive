---
title: "switched to dell from asus, overheating"
date: 2009-05-27
forum: Hardware
---

### Post by tedrampart on 2009-05-27
to sum up first:  my Dell D620 laptop, is running hot since I switched from an asus.  average idle temp is above 60C, and can get up to 95C by loading a couple programs.

I had previously been using an asus laptop (S62j), but it was very badly built and started cracking.  so I picked up a refurb dell.

I put my CPU, ram, and harddrive in it, and it booted up.  However, the cpu temp is running way too high for normal.  I ran sensors-detect and all it found was the coretemp module.  

the fans don't seem to be triggered at the right temps.

my question, is should I bother trying to work this out, or just reinstall, and let the installation configure with its setup scripts?

---

### Post by Dark_Stang on 2009-05-27
That sounds more like an issue with your laptop, not with your operating system. Refurbished laptops scare me.

---

### Post by tedrampart on 2009-05-27
I put a windows harddrive in, and its fine in windows, and I double checked the heatsink and everything.  so I don't think its an issue with the laptop, but rather the modules or settings.


I figure I should be at 45-55C normal use.

---

### Post by tedrampart on 2009-05-29
well I solved the issue.

I had previously added the nohz=off option in grub for the Asus, due to a bug that ran ksoftirq/1 at 15% of my cpu constantly.  

so, I removed that, and now running smooth and cool below 50C on the dell

---

