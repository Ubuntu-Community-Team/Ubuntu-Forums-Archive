---
title: "Having a touchpad issue"
date: 2019-05-26
forum: Hardware
---

### Post by Cognition on 2019-05-26
As the title states...this is my second time running Lubuntu on this computer. The same issues happened the first time. Luckily I'm able to get most of them fixed, but this time for some reason I've become stuck.
 
The problems start out with the cursor becoming unresponsive to the touchpad (the USB mouse still works). I use

```
[COLOR=#242729][FONT=Consolas]sudo modprobe -r psmouse
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo modprobe psmouse proto=imps[/FONT][/COLOR]
```

and that makes the cursor responsive to the touchpad again. But now the touchpad no longer detects my palm as I type. So I find a xorg.conf.d fix,

```
[COLOR=#242729][FONT=Consolas] Section "InputClass"[/FONT][/COLOR]        
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is re0commend on all Linux systems using evdev, but cannot be 
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
        MatchDevicePath "/dev/input/event*"
        Option "PalmDetect" "1"
        Option "PalmMinWidth" "4"
        Option "PalmMinZ" "100" 
[COLOR=#242729][FONT=Consolas]EndSection[/FONT][/COLOR]
```

and paste that over my old InputClass section. So this is now what my xorg.conf.d looks like. Just like on my last install, this is buggy. On the last install, palm detect would often quit working. I would go in Terminal and set PalmMinZ to 0 or PalmDetect to 0 then back to 1, and somehow that would work.

This install, having PalmDetect set to 1 often makes it so that my touchpad can't move the cursor. It seems this way, because the cursor will work if I set it to zero. Then sometimes, it will suddenly just start working with PalmDetect set to 0 in the Terminal again. It did start working just now as I was writing this. This is confusing and frustrating.

**Edit:** As I was fixing the code, the cursor again quit working, and left-click stopped working on both the touchpad and mouse. Help!

---

