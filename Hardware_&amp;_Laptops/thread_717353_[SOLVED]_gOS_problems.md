---
title: "[SOLVED] gOS problems"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by absolution87 on 2008-03-06
Hi, i know this is the ubuntu forum but any help is appreciated. 

I just installed gos 2.0.0 beta and it all installed fine. My first problem is the graphics. When it boots the screen is almost split in half and the top is at the bottom and the bottom is at the top. I had this same problem when i ran the ubuntu cd but when i installed it, it turned out fine. I then tried to run

```
sudo dpkg-reconfigure xserver-xorg
```

and change some settings there, i rebooted after changes and now i cant login at all, it goes to accept it then it just comes back to the gOS login screen.

Any help is appreciated

I'm trying to run it on a Compaq Armada M700 laptop

---

### Post by Scarath on 2008-03-07
To take it back to the way it was you will need to change your xorg.conf back to the origional one. When at the login screen, fall back to terminal mode (Ctrl + Alt + F1). Then go.

```
Sudo nano /etc/X11/xorg.cong.(hit tab and it will show you the backup made when you reconfigured)
```

Hit enter, while your in you xorg.conf you could scroll down to the devices section, check everything is in order, graphics drivers, your resolution, etc. 

Save the file as xorg.conf (overwriting the new one) and then restart X. That should get you back to the way it was before.

---

### Post by absolution87 on 2008-03-09
Ah you fixed my problem many thanks. Lol after all that i have decided to run ubuntu with the gos manager over the top. Well see how it goes, i like the power of ubuntu with the look of gos. Thanks again

---

