---
title: "[SOLVED] URGENT! Accidentally changed graphics card driver and graphics won't show"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by spyder0080 on 2007-10-19
Hello all,

I was trying to get desktop effects working in Gutsy by seeing if changing my graphics card driver would work. Unfortunately, when I did then I ended up losing my graphics capability. Basically, when I use Ubuntu now, I get a terminal-like interface instead of a GUI.

Can you help me change it back? I originally had the default driver set for ATI cards before I changed it. Also, how would I get desktop effects working?

Thanks!

---

### Post by frodon on 2007-10-19
When you are with your terminal interface type this command :
```
sudo dpkg-reconfigure xserver-xorg
```It will reconfigure your screen configuration.

If it don't work post back your problem here and we will try other things.

---

### Post by spyder0080 on 2007-10-19
> **frodon said:**
> When you are with your terminal interface type this command :
```
sudo dpkg-reconfigure xserver-xorg
```It will reconfigure your screen configuration.

If it don't work post back your problem here and we will try other things.

thanks, it worked!

I wasn't really sure which options to pick and to enter, so I left most of the options blank and/or default. Is that ok?

also, i've tried again to get visual effects working but it still won't work. any idea why?

---

### Post by frodon on 2007-10-19
I'm not expert for these questions but to help you on this users will need that you post your xorg.conf file.
You can use the following command to open it :
```
gedit /etc/X11/xorg.conf
```

---

