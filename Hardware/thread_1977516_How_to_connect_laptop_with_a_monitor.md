---
title: "How to connect laptop with a monitor"
date: 2012-05-10
forum: Hardware
---

### Post by toolm on 2012-05-10
I am using edubuntu 12.04. I have an Asus Eee PC 900HA laptop and I want to connect it with a Samsung SyncMaster 793DF monitor. I'd like to make the monitor the main displaying hardware. I don't want anything to be displayed on the laptop's monitor. But of course when I unplug the external monitor, the laptop's monitor should be the main one.

Is there any special, easy-to use and set software for this?


I already tried just plugging in the monitor without doing anything and it just displays the desktop image and the cursor. When I open some windows, they are displayed on the monitor and not on the laptop.

And I didn't know if I should've created this topic in this forum or in the Asus ubuntu one, so transfer it if this isn't okay.

---

### Post by wilee-nilee on 2012-05-10
Go to display and set it up that is where it's done.

---

### Post by toolm on 2012-05-10
I can't find anything. Is there any terminal command to access it? Or is there any software?

---

### Post by steeldriver on 2012-05-10
something like 

```
xrandr --output LVDS --off
``````
xrandr --output LVDS --auto
```maybe?

---

### Post by idoitprone on 2012-05-10
> **steeldriver said:**
> something like 

```
xrandr --output LVDS --off
``````
xrandr --output LVDS --auto
```maybe?

LVDS is your own laptop monitor

type 

```
xrandr -q
```

to get the list

If it is Vga
It is mostley likely

```
xrandr --output VGA1 --auto
```

[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

