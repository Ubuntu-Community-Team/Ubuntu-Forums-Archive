---
title: "General system performance monitor"
date: 2014-10-24
forum: Hardware
---

### Post by mark-lamorey on 2014-10-24
Does anyone know of a good system monitoring program with a good graphical display.
Something that would show CPU / Memory load , temperatures, voltages, etc ...

---

### Post by tgalati4 on 2014-10-24
I use *htop* for process monitoring:

```
sudo apt-get install htop
```

For temperatures, I place some instrument applets on my panel.

---

### Post by mark-lamorey on 2014-10-24
HTOP is nice, I see how it is a refined version of top.
Any thoughts on a more reduced metered version, something that I can pin in my screen ?

---

### Post by tgalati4 on 2014-10-24
[Conky]("https://help.ubuntu.com/community/SettingUpConky") is the mother of on-screen displays.

[Pick one]("https://www.google.com/search?site=&tbm=isch&source=hp&biw=1280&bih=703&q=conky+desktop&oq=conky+desktop&gs_l=img.3..0j0i24l3.1792.3983.0.4608.13.9.0.3.3.0.206.1129.0j5j1.6.0....0...1ac.1.56.img..4.9.1142.nfLCLvCUXxE") and then post it and ask how to get that look.

---

### Post by mark-lamorey on 2014-10-27
Is there a way of using CONKY to get information up into "menu bar".

I have used "System Load Indicator" in the past but it seems to be crashing and rather than debugging making a custom one might be interesting.

---

### Post by tgalati4 on 2014-10-27
No, Conky is its own application and it draws to the background.  There are several gnome applets that display on the panel.  Just right-click on the panel, "Add to Panel", then choose the applet you want displayed.  You can have load graphs, voltages, temperatures, etc.

---

### Post by mastablasta on 2014-10-28
gkrelm is another one for a quick look and if you do not want to have conky splashed over desktop all the time.

---

### Post by mark-lamorey on 2014-10-29
gkrelm is nice - I am not able to add it to the panel though.
I'm on 14.10

---

