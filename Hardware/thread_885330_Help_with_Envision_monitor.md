---
title: "Help with Envision monitor"
date: 2008-08-10
forum: Hardware
---

### Post by cod4beast on 2008-08-10
Well after reformating my hardrive and removing windows i deleted my monitor drivers.  Ubuntu worked perfectly before removing windows that had the drivers but now it wont go past 800x600 resolution even though the proper setting is 1024x720 or something like that i cant remember.  I have installed the program 915resolution and it worked for about a day but now it wont.  I have an envision monitor, if anyone who has had a similar problem or knows how to fix this, help wou ld be most aprreciated because i realy dont want to have to use windows or another distro just because i have a monitor that isnt supported

---

### Post by cariboo on 2008-08-10
You are going to have to set your horizontal and verical refresh rate in /etc/X11/xorg.conf.

Have you tried in recorvery mode:

```
dpkg-reconfigure phigh xserver-xorg
```

To enter recovery mode press esc at the grub prompt then from the menu choose recovery mode.

Jim

---

### Post by cod4beast on 2008-08-13
thanks but i fixed it... after reinstalling ubuntu (i got so frustrated I tries to go back to windows) but after the same kind of problem happened in windows after i installde the drivers i realized i must have the wrong ones so I reinstalled ubuntu and then nvidia drivers in the how to guide.  This led to a dialog box apearing allowing me to configure what drivers it should use.  I clicked generic monitor with the correct resolution because envision isnt supported and the experimental intel drivers.  They work perfectly now.

---

