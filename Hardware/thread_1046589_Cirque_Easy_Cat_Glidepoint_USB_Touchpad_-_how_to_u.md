---
title: "Cirque Easy Cat Glidepoint USB Touchpad - how to use advanced features?"
date: 2009-01-21
forum: Hardware
---

### Post by perixx on 2009-01-21
Hello!


I've been trying to figure out, how to access enhanced features of my external **Cirque Easy Cat Glidepoint USB** touchpad. 
By default, all basic functions work: click, doubleclick, corner-rightclick and vertical scrolling. But the standard accelleration and speed settings are too raw to make the pad a sensible mouse replacement. The Windows driver allows for a wide varietey of settings, so it can be configured to satisfy any needs.

There's hardly info around, on how to activate extended settings for (Cirque) Glidepoint devices for Linux, and if, mostly outdated and/or not applicable to an USB device (dedicated to PS2), like this thread:

**[http://ubuntuforums.org/showthread.php?t=417492&highlight=glidepoint+cirque&page=4](http://ubuntuforums.org/showthread.php?t=417492&highlight=glidepoint+cirque&page=4)**

All facts indicate that 'ALPS Glidepoint' touchpads are covered by the 'synaptics' touchpad driver at least to some extent. And they are based on the same hardware modules than the original Cirque products. Obviously, some people managed to get their touchpads to work, so it seems, especially internal laptop pads and PS/2 devices.    

So, the question is, how could I make use of the 'synaptics' driver to apply enhanced touchpad configuration settings? And where can be useful information obtained, about those settings?

Here's the output of 'udevinfo' and 'cat':
```
udevinfo -a -p `udevinfo -q path -n /dev/input/event4`
cat /proc/bus/input/devices:

[http://pastebin.com/mdc0e50f](http://pastebin.com/mdc0e50f)

```

Please help!


perixx

---

### Post by perixx on 2009-01-23
*bumpthis*

---

### Post by perixx on 2009-01-25
Doesn't really anybody have a clue?

*sigh*

---

### Post by drewm1980 on 2010-09-02
I'm working on getting my SmartCat working Debian Lenny...  I'm getting the impression that the synaptics driver just doesn't recognize the SmartCat hardware.

My device does show up in:

cat /proc/bus/input/devices

as "Cirque Corporation USB Glidepoint" and is getting assigned Handlers mouse1 and event1.

After spending some time modifying /etc/X11/xorg.conf according to the manual and starting the xserver manually, I'm getting messages like:

Touchpad no synaptics event device found
Query no Synaptics: 6003C8
(EE) Touchpad no synaptics touchpad detected and no repeater device
(EE) Touchpad Unable to query/initialize Synaptics hardware
(EE) PreInit failed for input device "Touchpad"

Note that the touchpad does work smoothly, has right edge scroll, upper right corner right click tap, has click tap all enabled out of the box.   I'm trying to figure out how to turn all these 1990's era touchpad features off and at least get some sort of two-finger scrolling emulation working.  

I'm not sure how to prove this, but I suspect the hardware is just presenting itself as a standard mouse and implementing the extra features internally.

---

### Post by perixx on 2010-09-26
> **drewm1980 said:**
> I'm working on getting my SmartCat working Debian Lenny...  I'm getting the impression that the synaptics driver just doesn't recognize the SmartCat hardware.
...
I'm not sure how to prove this, but I suspect the hardware is just presenting itself as a standard mouse and implementing the extra features internally.Hello drewm1980,

that's pretty much the same experience I've made so far and I've been giving up using the pad because of that annoying 'lag'-effect due to the same reasons. There's no specific features support in the synaptic driver for cirque pads and there won't be any, unless you find a friendly driver coder over at the xorg irc chat that is willing to take care of it - and if you're willing to provide him with the neccessary information. This kind of hardware is simply too exotic.

greetz,
perixx

---

### Post by jampe on 2010-09-27
I have an issue very similar to yours, but with an "Ortek Smart Pad" from Hong Kong. The only pseudo-solution I can think of, is to somehow convince xorg that it's not supposed to handle like a mouse, but like the built-in touchpad of a laptop.

The thing is, I have no idea how to approach this, and I'm not getting any answers when asking in here.

..maybe there is something useful in the Windows drivers? I'll dig a little deeper, I'd hate to give up on this.

---

### Post by perixx on 2010-10-06
Hi jampe,

as I said, you can try to catch some Dev over a the Xorg IRC chat and sort out the driver problem with his help.

regards,
perixx

---

### Post by jampe on 2010-10-07
Thanks for the tip. All I'm being told there is that it's impossible, though.. But it works for the built-in touchpad. Some rudimentary hack must be possible.

---

### Post by perixx on 2010-10-17
If you find one, please let us know :)

---

### Post by jampe on 2010-11-11
[post removed]

---

### Post by jcwx86 on 2010-11-29
I have an identical issue with my Circue Easy Cat USB touchpad on 10.04.

---

### Post by WebWatch on 2011-01-21
I also have Easy Cat USB which was working fine without special features in 9.10 but in 10.04 when I plug it in it and other pointing devices will only single click on task bar and no where else, I have to unplug it and launch terminal from alt+f2 and cmd restart (sudo shutdown -r 0)

I'm running Sony Vaio with AlpsPS/2 ALPS GlidePoint built in so I assume there's a conflict

---

### Post by WebWatch on 2011-01-21
IGNORE THIS POST
Had to use non quick reply so I could subscribe to the thread

---

### Post by robertbub on 2011-06-26
Did anyone ever figure this out?

For me, unlike the original poster, I'd like to know how to change the width of the scrolling area on the touchpad.  It just seems to have an evdev driver, which doesn't allow such customization.

---

