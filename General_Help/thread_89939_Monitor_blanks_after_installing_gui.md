---
title: "Monitor blanks after installing gui"
date: 2005-11-13
forum: General Help
---

### Post by Keshyden on 2005-11-13
I just installed a GUI (xfce) on an old Thinkpad and now I can;t get the monitor to show up. It worked with the server installation. Then I upgraded to  a GUI and nothing shows up.

---

### Post by jaddison on 2005-11-13
[QUOTE=Keshyden]I just installed a GUI (xfce) on an old Thinkpad and now I can;t get the monitor to show up. It worked with the server installation. Then I upgraded to  a GUI and nothing shows up.[/QUOTE]

It sounds like your settings for your video are too high for the screen to use - to prevent it from 'blowing up', it just shuts down.  You'll have to adjust your xorg.conf file, presumably.  Isn't there an automated way to do this, community?

Sorry I couldn't help more - try searching for xorg.conf editing or something.  Good luck!

---

### Post by aysiu on 2005-11-13
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jaddison on 2005-11-13
[QUOTE=aysiu]```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

Giddyup!  I knew someone would have the answers! ;)

---

