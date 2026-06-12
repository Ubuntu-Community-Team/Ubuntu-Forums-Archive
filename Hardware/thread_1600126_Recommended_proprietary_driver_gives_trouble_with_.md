---
title: "Recommended proprietary driver gives trouble with two screens"
date: 2010-10-18
forum: Hardware
---

### Post by JolleSax on 2010-10-18
Forgive me for not knowing the obvious, but I'm  completely new to Ubuntu. I just installed the 10.04 64bit standard version from CD  as a dual boot next to Windows 7, but I can't get my graphical setup up  and running like on Windows. 

The setting : 
- A graphics card ATI Radeon HD4350
-  Two Belinea monitors, of which one recognized (model 10 17 28 ) and one  not (model 10 17 51). The latter one is also not recognized by Windows7,  but it is called "non-PNP generic monitor" there and has the correct screen  resolution (1280x1024).

Ubuntu does not allow me to select the  correct resolution (maximum is 1024x780), but instead urges me to  install the proprietary driver ATI MAD FGLRX graphics. After I've done  so, I restart. At start, the unrecognized screen tells me it recieves an incompatible video mode. I  check, and it turned out Ubuntu has set the frequency at 43Hz. After changing this  to 60Hz in the setting I get a screen with the correct resolution, but now the whole desktop is behaving very strange :

- I can't hover from one screen to the other unless I click on the screen first. The cursor seems blocked by an invisible wall at the upper left border of the right screen. After I go back and click somewhere in the left screen, I can move the cursor over both screens.

- If I open a menu or dialog box, it stays on the desktop unactive like a "burnmark". It doesn't react, it just displays. Computer doesn't freeze, I can keep on working and even activate the same menu again from the bar to start up whatever application. But the image of the menu stays on the desktop, as do message boxes.

-  after startup, the "recognized" screen is garbled in tiny little  squares or showing some messed-up leftovers from the last screen before  shutdown.

Uninstalling the proprietary driver brings me back to start: correct display, but wrong resolution.

I looked through the internet  searching for some open source driver that could make this work, but couldn't find a thing. I  don't need high graphic 3D rendering stuff, I just need a calculating workhorse with a screen I can look at for 8  hours in the right resolution. Anybody an idea what I can try to get  this work?

PS : I've read a lot about a xorg.conf in etc/X11 or so that I had to change manually, but I couldn't find that file. I also read a lot about Nvidia, but that's an unknown for me.

---

