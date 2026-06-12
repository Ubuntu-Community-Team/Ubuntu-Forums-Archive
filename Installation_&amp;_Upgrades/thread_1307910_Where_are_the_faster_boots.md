---
title: "Where are the faster boots?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by hambone79 on 2009-10-31
I upgraded two systems from 9.04 to 9.10 yesterday and I'm very happy overall. I did not have any of the issues that a lot of the others seem to be having, but I do have one extremely annoying problem. Every since I upgraded, both of my Ubuntu machines are extremely slow to boot. Before it took less than a minute to boot both systems, now it is taking about 10 minutes on one machine before I see the login screen and about 5 minutes on the other machine. What the f? I thought Karmic was supposed to have insanely fast boot times, but all I'm seeing is a much slower boot process. What am I missing?

---

### Post by t.rei on 2009-10-31
I'm having similar issues.
My booting now works like this:
Poweron... wait... Grub loading... waiting waiting waiting... finally grub comes up... (grub2?) booting, splash is there... slash is gone... looking at a blinking cursor... seeing console login... finally kdm pops up... 

This is taking a good long time.
Since my system is just configured the way I want it - is there any way, apart from reinstalling, to get this cleaned up?

Thanks.

---

### Post by hambone79 on 2009-11-01
I just discovered that the xsplash packages did not install correctly for some reason. After uninstalling and reinstalling, I have fast boot times.

---

