---
title: "CD playback"
date: 2005-12-03
forum: General Help
---

### Post by mclen on 2005-12-03
My standard CD player has stopped functioning. When I insert a CD and it starts autoplay, the CD player application launches, but doesn't play tracks at all. Then I try to press play manually and get the same result. How can I correct this?

---

### Post by gonçalo on 2005-12-03
what is the Ubuntu version you are using? 

If it's soundjuicer that pops up when you insert the cd, have you tried changing the cd on edit/propreties?

On other apps, like bmp you can go BMP preferences/Plugins /Media

select CD Audio Plugin and click Preferences

there you will be presented with some choices.

I had the same problem as you and all I had to do was change from /dev/cdrom0 to /dev/cdrom1 in the Device: of tab **drive 1**


hope this helps.

---

