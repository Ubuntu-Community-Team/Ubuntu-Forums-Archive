---
title: "Assign additional mouse buttons in Natty"
date: 2011-05-12
forum: Hardware
---

### Post by kaktus621 on 2011-05-12
Hi,

I have a Logitech MX Revolution which has some additional keys that I would like to use in Ubuntu 11.04. After editing the xorg.conf, those keys are recognized by the system (can be tested by using "xev|grep button"). However, I can't find any way to assign those buttons in the Unity shell in Natty.

The "Keyboard Shortcuts" menu seems to react only to keyboard shortcuts (I think that's the reason for its name :P) but there is any "Mouse Shortcuts" menu or something like that.

To be more specific, I want to bind the "Expose" like dashboard (Shift + Alt + Arrow Up) to a mouse key.

How to do this?

---

### Post by nepeter on 2011-05-18
Bump.

I would also be interested in learning how to do this.  I want to assign copy and paste to the two extra buttons on the side of my mouse (8 and 9 according to xev/xinput).  I know they do forward and backward functions, but I'd rather have them copy and paste.  

Surely there is a way to assign some key combo to a mouse event in X?

---

### Post by nepeter on 2011-05-18
Oops.  Another fifteen minutes of googling lead me to [http://ubuntuforums.org/showthread.php?t=316441]("http://ubuntuforums.org/showthread.php?t=316441").  

I tried the first thing mentioned and installed btnx and btnx-config.  After five minutes of setup and playing around, I now have copy and paste (via CTRL-c and CTRL-v) activated by mouse buttons.  Having a button do Shift+Alt+Arrow Up should work, as well.  Good luck!

---

