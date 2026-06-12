---
title: "Need help getting unique wallpapers on workspaces"
date: 2008-09-10
forum: General Help
---

### Post by pwaugh on 2008-09-10
Hi,

After updating Compiz, with the new Wallpaper option in CCSM, and adding 4 wallpapers there, I still see the same wallpaper on all 4 workspaces.

Also, while I have setup the 3D cube and have it working, I see it from the inside, but on the YouTube video on the setup page, it shows it from the outside.  How do I do that?

Patrick

---

### Post by JECHO on 2008-09-10
> **pwaugh said:**
> Hi,

After updating Compiz, with the new Wallpaper option in CCSM, and adding 4 wallpapers there, I still see the same wallpaper on all 4 workspaces.

Also, while I have setup the 3D cube and have it working, I see it from the inside, but on the YouTube video on the setup page, it shows it from the outside.  How do I do that?

Patrick

to have an exterior view of the cube you need to go to ccsm and click the desktop cube option. then click the behavior tab and uncheck the "inside cube checkbox

---

### Post by Genius314 on 2008-09-10
To get the cube from the outside:
Go to CCSM, in the Desktop Cube plugin, click on the "Behaviour" tab, and uncheck "Inside Cube."


To get the four wallpapers (Note: You won't have any desktop icons if you do this):
1. Open a terminal and type gconf-editor.
2. Go to apps/nautilus/preferences and uncheck "show_desktop."


Hope that helps. :)

---

### Post by pwaugh on 2008-09-10
> **JECHO said:**
> to have an exterior view of the cube you need to go to ccsm and click the desktop cube option. then click the behavior tab and uncheck the "inside cube checkbox

OMG, I feel stupid now, haha.

Still, in the video I've seen, the cube is "zoomed" so it is much smaller than when I see it on my system.

Patrick

---

### Post by pwaugh on 2008-09-10
> **Genius314 said:**
> To get the cube from the outside:
Go to CCSM, in the Desktop Cube plugin, click on the "Behaviour" tab, and uncheck "Inside Cube."


To get the four wallpapers (Note: You won't have any desktop icons if you do this):
1. Open a terminal and type gconf-editor.
2. Go to apps/nautilus/preferences and uncheck "show_desktop."


Hope that helps. :)

Works like a charm.... but seems like there should be a way to not lose desktop icons.

In all honesty, I like a clean desktop though, so I'll give this a try I guess.  With the object dock, and the panel I use, I'll probably like this.

Patrick

---

### Post by JECHO on 2008-09-10
> **pwaugh said:**
> OMG, I feel stupid now, haha.

Still, in the video I've seen, the cube is "zoomed" so it is much smaller than when I see it on my system.

Patrick

haha no worries... you can set the zoom of the cube too. go to ccsm and click cube rotation and then use the slide to specify how far/close you want it when rotated. haha i know you probly feel stupid again :lolflag:

---

### Post by pwaugh on 2008-09-10
> **JECHO said:**
> haha no worries... you can set the zoom of the cube too. go to ccsm and click cube rotation and then use the slide to specify how far/close you want it when rotated. haha i know you probly feel stupid again :lolflag:

How did you guess!!!  :lolflag:

Finally have it the way I wanted.  Thanks guys.

I really love Ubuntu, and am really glad I tried it!  I used Solaris years ago, and can't believe how far things have come.

Patrick

---

