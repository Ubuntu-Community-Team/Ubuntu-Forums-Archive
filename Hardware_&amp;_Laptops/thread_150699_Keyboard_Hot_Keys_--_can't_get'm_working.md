---
title: "Keyboard Hot Keys -- can't get'm working"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2006-03-26
So I won a bluetooth keyboard & mouse on ebay, they're great (a bit slugish compared to regular wireless devices but I can sit in bed across the room and they work).

The problem is I can't get any of the keyboards media hot keys to work.  On all of my other keyboads I could use gnome's 'keyboard shortcut' editor and everything was a-ok.  This keyboards hot keys don't even respond.

I've tried them in gnome's keyboard shortcut editor
command line (no response) 
and xev in a terminal...... nothing!!!

It's a Microsoft Wireless product, I've tried all of the keyboard maps in 
system--> prefrences--> keyboard

nothing.  

Do I have to restart X every time a change the map in gnome?[IMG]http://www.microsoft.com/presspass/images/press/2002/10-15OpticalMousekb-sm.jpg[/IMG]

---

### Post by Sboulema on 2006-03-26
Try Keytouch: [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)
Worked for me :D

---

### Post by greenwom on 2006-03-26
I already installed it (forgot to mention that) and didn't have much luck.

Can you give any pointers on keytouch?  I'll play with that some more.

---

### Post by wsmoser2004 on 2006-03-30
Sorry, I can't help much with Keytouch, but I use something called HotKeys which supports certain multimedia keyboards.  I believe it is in the repositories somewhere.  It may or may not support your keyborad, but if it does, it probably will support most if not all of your hot keys, plus it has on-screen display :-P.

---

### Post by arczi on 2006-03-30
I have a different problem. I have two sound cards, one on the motherboard hw:0,0 and the the other, a soundblaster pci card, at hw:1,0. I've set /etc/asound.conf so that the second is the default, but hotkeys still insists on changing the volume/muting the first, non-default one. Any idea how to get hotkeys to change the volume on my card of choice?

arthur

---

