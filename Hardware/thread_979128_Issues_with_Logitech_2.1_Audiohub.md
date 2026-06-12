---
title: "Issues with Logitech 2.1 Audiohub"
date: 2008-11-11
forum: Hardware
---

### Post by invictuz on 2008-11-11
Hey there, I've been having problems with my usb speakers/hub combo.

Whenever I plug it in (in ubuntu or from startup), it blasts the login song, as well as furiously ticking.  It'll keep up the ticking for a few seconds afterwards then just stop being a speaker.  The hub aspect works just fine, however.

I tried different means of making it my default sound output, but it wouldn't play any sound, unless I went through System->Preferences->Sound and tested the output, in which it was full blast and still ticking.  I have no found a way to alter the volume whatsoever.

A strange thing though, once it's plugged in and beyond the ticking and whatnot, the knob the would usually control the volume for the speaker will control the volume to the laptop sound output.

Any Help will do!

Thanks

---

### Post by 11hjpphty76lkjj on 2008-12-06
This has been reported before....look here for a possible answer..although I haven't tried it yet..

[http://ubuntuforums.org/showthread.php?p=6322293#post6322293](http://ubuntuforums.org/showthread.php?p=6322293#post6322293)

Sorta nervous about compiling my own kernel.

---

### Post by CJay554 on 2008-12-25
I don't think your suppose to copmile your own kernel... More in the likes your suppose to edit a file on the system to "uncheck" those two options stated, though i don't know where to find this "Device driver -USB support - EHCI HCD" as Archlinux has a different system control than Ubuntu..

Anyone know how i can edit these files directly and edit the config?

---

### Post by monkeys on 2009-02-16
[http://ubuntuforums.org/showthread.php?t=806555](http://ubuntuforums.org/showthread.php?t=806555) <- This thread is related and seems to have the steps to the EHCI solution, although I haven't tried it yet. Has anyone figured it out yet?

---

### Post by mrwinalot on 2009-08-17
Anyone please? I'm having the same problem. Nothing seems to work for me:(

---

### Post by corq on 2009-10-06
I can happily confirm, in Karmic Koala this is *FIXED* for me and these sound awesome (and my netbook has a spare usb hub!)

This too was a frustration of mine and I just wouldn't part with these speakers. kernel version "2.6.31-10-generic #35-Ubuntu SMP"

---

