---
title: "I set Gnome resolution far too high"
date: 2008-11-04
forum: General Help
---

### Post by Johnsie on 2008-11-04
I changed the resolution in gnome to the highest setting via the preferences option. Now every time gnome starts the resolution is far too high and i cant click or see anything other than part of the wallpaper.

How can I get the resolution back to something normal or the default? Is there a file in my /home folder that holds my resolution preferences?

---

### Post by Paul41 on 2008-11-04
You can press ALT->F1 at the log in screen. This will take you to a command line. From there you can log in and run the following command.

```
sudo dpkg-reconfigure xserver-xorg
```

This will allow you to reset you settings.

---

### Post by Something Other on 2008-11-04
Hey all:
I recently installed Intrepid Ibex and am having similar issues that I had in Gutsy Gibbon.  I have a 46" 1080p lcd tv that I have my computer hooked to via my Nvidia video card through a DVI to HDMI cable.  By default, Ubuntu has the resolution so large that I cannot see anything other than the desktop wallpaper.  I have tried going into terminal and using the nvidia-settings command and adjusting the different resolutions but when I lower it all I get is the same thing just zoomed in.  Does anyone have a suggestion on how I can adjust my settings so I can have a normal desktop again?  Thanks in advance.

---

