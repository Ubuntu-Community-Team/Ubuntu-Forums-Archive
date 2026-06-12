---
title: "presentation pointer ( ppt.)"
date: 2009-06-17
forum: Hardware
---

### Post by geogur on 2009-06-17
I bought a Targus presentation pointer when I went to there site they claim there is no driver needed . But on my eeepc it will not work can I fix this . I want to run Linux and do my presentation using open office , and also want the use of my air mouse ( Targus AMP06CA ) . this device should plug and play but on a Ubuntu or a Zandros machine it will not work . is there something I can do to fix this .

---

### Post by JaseP on 2009-08-15
I have the Targus PAUM30U (2 of them actually). I use them as mice with my Multimedia PCs, running Jaunty...

The presentation pointers produce an output similar to that of keyboards... Like extended keyboard events... Your best bet is to either Google for your particular model for some sort of extended keyboard hot-key configurer, or look at the optins in OpenOffice Impress to see if it supports the devices...

You MIGHT need to pair the device with its adapter... The often loose their pairings, particularly with a lot of 2.4 GHz devices around...

The best recommendation, though, is to ditch the one you got for the model I have (it has a mouse mode and a presenter mode with built in laser pointer, buttons emulate mouse buttons or certain keyboard combos, depending on the toggle switch position), or to just get a Logitech wireless mouse... Logitech can be real s-o-b's when it comes to Linux support, but their stuff just tends to work.

Another thing to look at is whether you are running Compiz. Compiz will intercept certain hotkey assignments that you set in regular Gnome (and probably KDE too).

---

### Post by amit_m on 2009-11-02
[http://dougsland.livejournal.com/65872.html](http://dougsland.livejournal.com/65872.html)

That should help you. It helped me with Targus AMP03US. I just did this

$ sudo dmesg


That simple. Everything started working.

---

