---
title: "Stuck in 800x600 resolution"
date: 2008-07-16
forum: General Help
---

### Post by alcairn2030 on 2008-07-16
So I installed Ubuntu today. So far I like it except for one thing. I cant change from 800x600. How do i fix this?

3D Banshee 16mb Vid Card
433mhz CPU
256mb RAM

---

### Post by kunixos on 2008-07-16
you need to be sure your monitor supports resolutions higher than 800x600 first, then ensure you have the proper drivers for your Banshee card (should already be good).

you might end up having to modify the /etc/X11/xorg.config file, but check those two things out first. you seem to have a lower-end computer, so it's worth making sure it'll work.

Hope this helps!

---

### Post by alcairn2030 on 2008-07-16
yes i was running Win XP on this earlier today at 1024x768. Now what?

---

### Post by alcairn2030 on 2008-07-16
omg someone respond please...this is pissing me off

---

### Post by iaculallad on 2008-07-16
> **alcairn2030 said:**
> omg someone respond please...this is pissing me off

Try to post your xorg.conf file if it could help resolve your issue:

```
cat /etc/X11/xorg.conf
```

---

