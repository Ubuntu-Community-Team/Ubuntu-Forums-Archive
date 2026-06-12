---
title: "A few questions on desktop customisation"
date: 2008-07-13
forum: General Help
---

### Post by rustix on 2008-07-13
Hi.,

I'm considerably new to Ubuntu (and linux) and I was wondering whether each virtual desktop/screen in ubuntu could have a different background image??

also i've seen on certain machines when the user switches virtual desktop/screen it rotates in a cube.. how do i do so?

---

### Post by chris4585 on 2008-07-13
there isnt a option by default to make each work space have a different background but there's some applications that change that.

As for the cube question.

right click on your desktop, go to the visual effects tab, select extra, if it says it cannot be enabled, then go to system > admin > hardware drivers and see if you can install a xgl graphics driver for your video card, if there isnt a option then you're out of luck.  If it does enable go to the terminal and type in:

```
sudo apt-get install compizconfig-settings-manager
```

go to system > prefs > Advanced desktop customization or something, select the cube and rotate cube plugins, and on your desktop rotate your cube by scrolling.  

hint: if you want a cube on your switcher applet (work space switcher) on the gnome panel right click and select preferences, and make 4 desktops

all done :)

---

### Post by rustix on 2008-07-13
looks like i'm out of luck.. there isn't a xgl graphics driver for my video card :(
thanks though

btw could you tell me the name for an app which lets me have different background images??

---

### Post by chris4585 on 2008-07-13
well there might be a xgl driver for your video card, but it might be hard to find/install, and i've only heard of such programs sorry, google is your friend! :P

---

### Post by rustix on 2008-07-13
lolz.. thanks for your help dude :)

---

### Post by finer recliner on 2008-07-13
> **rustix said:**
> I was wondering whether each virtual desktop/screen in ubuntu could have a different background image??


Gnome does not give you this option unfortunately. This application can achieve what you want though:
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

---

### Post by sayakb on 2008-07-13
Try wallpapoz: [http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

EDIT: finer recliner beat me on that.. :)

---

### Post by chris4585 on 2008-07-13
yeah, it sucks when there isnt a xgl driver for your graphics card

---

### Post by rustix on 2008-07-13
thanks again to all :)

btw i figured a way to make the cube thing work as well as rotate.. :)

---

