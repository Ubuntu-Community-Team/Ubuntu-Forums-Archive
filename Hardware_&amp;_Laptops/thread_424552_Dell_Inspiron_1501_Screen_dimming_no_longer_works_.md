---
title: "Dell Inspiron 1501 Screen dimming no longer works (Feisty)"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by Tispho on 2007-04-26
It worked fine in edgy, 

I have 2.3.0 BIOS

Screen dimming with Fn keys do not work with feisty. 

is there a fix? 

sometimes when it does work, It jumps between dimmest and brightest only. 

sometimes it gets stuck in dimmest.

Also, does anyone know how to get knetworkmanger to automatically connect to a HIDDEN WPA PROTECTED router? I find that I have to enter my SSID and wpa key everytime I boot kubuntu to access the internet over WLAN.

---

### Post by nachotronics on 2007-04-29
I use gnome, but you could try doing this:
```
sudo kate /etc/modprobe.d/blacklist
```
and the adding "blacklist video" to the end of that file.
Reboot and try it out, as i said i use gnome, but this worked on my inspiron 6400

Hope this helps :wink:

---

