---
title: "Partial desktop displayed on HP 2133 Mininote"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by treunanen on 2009-07-14
Hi all,

I have just finished installing Xubuntu 9.04 on my HP 2133 Mininote. Everything seems to in order except my desktop is displayed only partially. No matter which resolution I apply ( even 800x600 ) the bottom and the right of my desktop are left out of the screen. When I check the synaptic package manager for OpenChrome drivers, it shows that it has already been installed.

My Xorg config is rather empty, buy still I am able to change to different resolutions its just that always the bottom and the right side of the desktop is left out.

Any ideas?

My xorg.conf

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by mrhobbeys on 2009-07-14
Sorry if this doesn't work, it does on other distros, but log out and then get to the terminal and type confx or xconf I haven't had to use that in Ubuntu but I know it works in some of the live distros I use to configure the xorg files.

---

### Post by treunanen on 2009-07-15
Unfortunately this command is not available on ubuntu. Any other ideas?

---

### Post by treunanen on 2009-07-16
Seems like this issue is related to the WLAN also and it has been reported as a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355918]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355918")

---

### Post by smash_it on 2009-07-18
im running ubuntu on my 2133 but probably you can use this solution for yourself aswell

pretty much everything worked out of the bex - except for the wireless. after using it the resolution was different - i don't know if this is the same problem as you are experiencing.

after modifying the xorg.conf it all worked well. you might want to follow the instructions under the link below - it worked for me so hopefully for you aswell

[http://www.linlap.com/wiki/hp+2133](http://www.linlap.com/wiki/hp+2133)

---

