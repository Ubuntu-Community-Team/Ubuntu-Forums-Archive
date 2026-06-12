---
title: "Wacom Intuos 5 touch ring not working Ubuntu12.04"
date: 2013-03-21
forum: Hardware
---

### Post by BcRich on 2013-03-21
This is a little odd because the touchring (used for scrolling) on my wacom intuos 5 works perfectly in Kubuntu 12.04, but for some reason it doesn't do a thing in Ubuntu 12.04 (both  x64)?
any suggestions, thanks

---

### Post by Favux on 2013-03-21
Hi BcRich,

Well in Kubuntu Precise you would be using the KDE Wacom tablet configuration system tool and in Ubuntu Precise you would be using the Gnome Wacom tablet applet.  Maybe the Gnome applet doesn't have a data file for your tablet in libwacom?  Is it correctly identified?  Or maybe that version of the applet (Gnome 3.4 or 3.6?) doesn't yet support touch rings?  Don't know for sure.

You can use a touch ring toggle script and bind the Button 1 (in the center of the touch ring) to the script:  [http://ubuntuforums.org/showthread.php?t=1380744&p=12547943&viewfull=1#post12547943](http://ubuntuforums.org/showthread.php?t=1380744&p=12547943&viewfull=1#post12547943)

---

### Post by BcRich on 2013-03-22
Hi Favux :)
Thanks for clearing that up.
The Gnome applet does seem to identify my wacom by it's correct name i.e. intuos 5
I'll have to take a look at your script sometime, there's quite a bit of info in there :)

---

### Post by BcRich on 2013-04-07
Hi just to follow up on this
```
xsetwacom set "Wacom Intuos5 touch M Pen pad" AbsWheelUp
xsetwacom set "Wacom Intuos5 touch M Pen pad" AbsWheelDown

```
solved the problem but I'm not sure if this will persist after reboot.

---

