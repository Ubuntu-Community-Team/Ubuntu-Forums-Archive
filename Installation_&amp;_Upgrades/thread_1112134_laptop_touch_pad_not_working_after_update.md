---
title: "laptop touch pad not working after update"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by luxerama on 2009-03-31
Hi everyone,
I have received a security update today, but as I have automatic security updates enabled I have no idea what was being updated. I just noticed the restart icon in the task bar.
However since the update my touch pad has seized  working (including the buttons corresponding left/right mouse) is there any way to reverse the update, or find out what has been update?

If you need any more info please let me know.

System:
Acer Aspire 5630
Ubuntu 8.10 (2.6.27-11-generic)

---

### Post by Mark Phelps on 2009-04-01
Ubuntu 8.10 changed the way that touchpads, keyboards, and mice are "read".  Previously, this was all done through entries in the xorg.conf file.  With 8.10, this was shifted over to HAL.

When I updated my tablet PC to 8.10, ALL that stuff quit working.  I was able to fix it by booting into a LiveCD and uncommenting the lines in my xorg.conf file (for touchpad, keyboard, and mouse) that had been commented out during the Intrepid update.

That may not fix it for you, but it's worth a try.

---

