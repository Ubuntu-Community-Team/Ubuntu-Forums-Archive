---
title: "Laptop's Fn key combinations"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by Copter on 2005-10-29
hi!

does anyone know how to enable / peronalize laptop's Fn key combinations? like Fn F6 to turn on wifi and so. the same thing goes to special volume keys. in winxp they are aliased with master volume but here i cant asign them to anything.

thanks for any info :)

copter :]

ps. its a LG GS50

---

### Post by davmac on 2005-10-29
Try System -> Preferences -> Keyboard Shortcuts. Click on the action you wish to change and then type the key combination you want to assign it to. It doesn't work for all key combinations on my Dell Inspiron 510m laptoip, but I can control the volume and a couple of other things.

Regards,

Dave Mac

---

### Post by Copter on 2005-11-06
thnx 4 help. i tried that but no luck. xev responds only to volume keys but i still cant assign them to anything.

copter :]

---

### Post by scubajeff on 2005-11-06
What's your notebook's model? Those Fn key combinations will generate ACPI events but not general keyboard events. So you need to load the appropriate kernel modules to read them.

---

### Post by Copter on 2005-11-10
its LG GS50. do you know which modules i should load for them to work?

thnx 4 help!

---

### Post by zonk on 2005-11-11
This is interesting. I do have the same problems on an LG LW40 and the FN-Keys are only partially working on my Laptop.

The FN-F6 turns of the wireless and it just worked, but most of the other keys aren't working.
I would be happy if someone had an  idea.



zonk

---

### Post by Copter on 2005-11-11
i forgot to mention - FN F5 (touchpad on / off) works also... but it is not seen by xev. volume up, down, mute are seen by xev... but are not asignable. strange, isnt it?

copter :]

---

### Post by zonk on 2005-11-13
Hi.

I just found something about acpi-events. I haven't had time by now to read it, but if you feel like:

[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

[QUOTE=Copter]i forgot to mention - FN F5 (touchpad on / off) works also[/QUOTE] 
It doesn't on mine. But that would be nice, it is a bit nasty typing a lot with the touchpad turned on..... 

> but it is not seen by xev ... strange, isnt it? 
No I don't think it is strange. As scubajeff already mentioned those keys produce acpi-events, and these are not seen by xev (as far as I know), but Volume up, down are not ACPI-Events, so xev can see them. I only wonder that you cannot asign them on your own.

CU

zonk

---

### Post by Copter on 2006-03-22
ive found thins link [http://www.cweiske.de/howto/xmodmap/allinone.html]("http://www.cweiske.de/howto/xmodmap/allinone.html"). what i did:
```


nano ~/.Xmodmap
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

xmodmap .Xmodmap
```done.

copter :]

---

### Post by phoenix5002 on 2008-02-02
I used that and found my Fn key is keycode 115, and F2 is keycode 68.
How can I make the key combination Fn+F2, do I just add the numbers together for 183?

---

### Post by Copter on 2008-02-08
Hi phoenix5002!

On my machine xev doesnt see my Fn key in any combination. Some combination works (like Fn+F5 for external monitor, Fn+F4 for susspend, Fn+Home/End for brightnes and couple of others) but they are stiil not visible to xev. Besides keyboard keys I have 2 special keys. These are vol+, vol- and mute (when pressed together). They are seen by xev. As far as I know you can assign commands to keys only when xev sees them. Xev has to print out exact key code like 64, 31 or so. If you want to make key combos from keys that are seen by xev than Xmodmap will not help you. You have to configure it in your desktop manager.

copter :]

---

