---
title: "inspiron 5150 fan running constantly"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by sage on 2005-05-07
I've noticed that the fan seems to be running constantly on my Dell Insprion 5150 laptop after installing Ubuntu.  The laptop packages are installed.  Any ideas ?  thks.

---

### Post by airhead on 2005-05-08
Does the output of "lsmod | grep speedstep" give you anything? I have a fairly wierd cpu in my laptop (5150 also) and Ubuntu didn't realise it was speedstep capable. I hacked the cpu detect script to load the corresponding speedstep module and it worked fine.

I'm guessing that speedstep support isn't being loaded and the cpu is consequently stuck at 100%. The Dell fan gets pretty annoying when you're running at 100% :roll:

---

### Post by sage on 2005-05-08
I think the speed step is working since I can hear it sometimes kick up a notch and step down - it is usually running at the slower speed - the problem is that it is just running hot all the time so the slower speed fan is running most of the time.  And yes the fan noise is really bothersome.  - The gnome opengl screen savers really kick up the fan.

---

