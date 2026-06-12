---
title: "Fake a higher resolution on small screen?"
date: 2008-07-21
forum: Hardware
---

### Post by coolaj86 on 2008-07-21
I have an 800x600 screen on an old clamshell iBook and after downsizing the desktop fonts and seeing that they were still readable I got the idea that I could probably fake a higher resolution, say 1024x768 on the screen and then all of the images would just be smaller too.

I saw that people are using [krdc on the eee]("http://forum.eeeuser.com/viewtopic.php?id=14588").

Any ideas about how I could do this through X11 or in gnome?

---

### Post by kerry_s on 2008-07-21
you could change the dpi, say like 75, perhaps smaller. that should make everything smaller.
not sure if it's supported on the mac but you can try using a virtual size, that will allow you to use 1024x768 by scolling the screen around.

xorg.conf:
Subsection "Display"
Depth 24
Modes "800x600"
Virtual 1024 768
EndSubSection

on my laptop i could make the 1024x768 be 1280x1024, but i preferred to just scroll side to side so i used 1280x768. scrolling takes getting use to.

---

### Post by coolaj86 on 2008-07-21
I'm running Debian, not OSX, so the virtual screen is supported.

The virtual screen with scrolling I'm familiar with and I may do that. At least then I can load applications that are bigger than my screen size.

I'm looking more for a scaled solution rather than a scrolling solution.

I just did some more googling with the term 'scaling' (I hadn't thought to do that before) and it seems that Windows, KDE, and OS X all have VNC clients that support scaling, but not Gnome.

:'(

---

### Post by kerry_s on 2008-07-21
if it's only scaling than setting a smaller dpi should shrink everything, i believe the default is 96 in debian, which makes it the same as windows, 75 would be what osx runs, so you might want something around 60 to equal 1024x768 size.

you should be able to set your dpi in your gnome settings, for system wide you need to edit your xorg.conf.

---

### Post by coolaj86 on 2008-07-21
Thanks, that's a nice tip. However, using the GUI tool in Gnome under System > Preferences > Appearance it only works for fonts, not for scaling the whole screen.

Does it scale everything if I edit /etc/X11/xorg.conf?
(I'm not at that computer right now)

According to [this blog]("http://linux-blog.org/index.php?/archives/227-KDE-and-Xorg,-Fonts-and-DPI.html") I should be able to calculate my desired display size and dpi something like this:

800x600 60dpi (effectively 1024x768 75dpi or 1280x960 96dpi)
Width = (800/60)*25.4 = 338.67
Height = (600/60)*25.4 = 254

```
Section "Monitor"
    #Appended to the end of this section
    DisplaySize    338    254    # 800x600 60dpi
EndSection
```

---

### Post by coolaj86 on 2008-07-24
Result: It scales fonts and menu bars that don't contain images.

Using scalable VNC through KDE's krdc looks like the only way to go for now, but Gnome's vinagre should add scaling support soon... maybe...

---

### Post by josvanr on 2011-03-10
this does it


xrandr --output LVDS1 --scale 1.2x1.2


(replace LVDS1 by your monitor; to find out type
only 'xrandr')


I don't understand why almost no one seems to be using this !
(at least, almost no posts on forums about this)

On my 12'' 1280x800 screen I just can't live without it. Using
gimp on that resolution for instance is virtually impossible. 
But with the scaling option I can use it with no problem.

Why isn't this option in the kde4 monitor settings ? The functionality
is there...........

josvanr

---

