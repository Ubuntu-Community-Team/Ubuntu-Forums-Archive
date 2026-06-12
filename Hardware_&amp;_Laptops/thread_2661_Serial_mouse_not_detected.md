---
title: "Serial mouse not detected??"
date: 2004-10-30
forum: Hardware &amp; Laptops
---

### Post by dude_a_b_c on 2004-10-30
Installation proceeded fine, and was presented GDM greeter.  But mouse cursor stays stuck in center of screen.

Mouse is : Logitech 3 button serial type, and works fine with mandrake and fc2.

how to configure mouse ?

adviise/suggestions grtly appreciated

thanx in advance

---

### Post by mercurus on 2004-11-03
[QUOTE=dude_a_b_c]Installation proceeded fine, and was presented GDM greeter.  But mouse cursor stays stuck in center of screen.

Mouse is : Logitech 3 button serial type, and works fine with mandrake and fc2.

how to configure mouse ?

adviise/suggestions grtly appreciated

thanx in advance[/QUOTE]

I'd imagine it hasn't detected it properly, or you didn't answer its question when it installed X correctly.

You can run xf86config (text-based) or xf86cfg (GUI) to re-configure your XFree86 configuration, or edit it manually by editing /etc/X11/XF86Config-4 .

You'll want to change the lines that say something like:
```

        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"

```
to use a serial port.
```

        Option          "Device"                "/dev/ttys0"
        Option          "Protocol"              "Auto"

```
(Depending on the serial port to which your mouse is attached)

I recommend xf86cfg.

Cheers
mercurus

---

### Post by dude_a_b_c on 2004-11-17
Thanks for the advice.
However when I reconfigure the mouse (it is connected to ttys0), the pointer still refuses to budge 

Any suggestions please? 

Thanks in advance.

---

### Post by terminal on 2005-01-22
Exactly same mouse and same prob here :(  .


Plz help

---

### Post by Pcniatic on 2005-01-30
it work for me, but note that the serial port is /dev/ttyS0 not /dev/ttys0.
Hope it helps,

---

### Post by thestarman on 2005-02-03
If your mouse still doesn't work, instead of using "Auto" for the **Protocol**, instead use: "**Microsoft**" (funny how that's even a mouse-protocol name now!). My mouse Device is at "ttyS0" which is the first serial port (or COM1).  Anyway, I used the 'pico' editor in a Terminal window, and *as soon as I saved the change * I was able to start using the mouse on my Ubuntu Desktop!  :D 

Daniel (aka, The Starman).

---

### Post by sga1980 on 2007-07-25
Same prob. for me, using Ms Virtual PC 2007, but with an XP VM that port works fine, I modified xorg.conf as you suggested even tried with "Microsoft" protocol, but no way.

Suggestions?

Thanks a lot in advance, best regards!

---

### Post by Cariboo1938 on 2008-02-07
> **dude_a_b_c said:**
> Thanks for the advice.
However when I reconfigure the mouse (it is connected to ttys0), the pointer still refuses to budge 
Any suggestions please? 
Thanks in advance.
Hello dude_a_b_c,
My Serial mouse is connected to the 'COM1' plug on the motherboard and I just ran into the same problem. I suppose you solved the case and I wonder if you, please, could post HERE what you did have to do to get the serial mouse working?

---

### Post by Cariboo1938 on 2008-02-08
Hello dude_a_b_c, never mind...don't worry...I changed the xorg-file that way:
> Entry in file /etc/X11/xorg.conf to configure the "Logitech MouseMan Serial" mouse, 
which is connected to the 'COM1' plug on the motherboard:

Section "InputDevice"

        Identifier      "Mouse1"
        Driver          "mouse"
        Option          "Device"        "/dev/ttyS0"
        Option          "Protocol"      "Microsoft"
        
EndSection
Now the serial mouse works just fine.:guitar:

---

