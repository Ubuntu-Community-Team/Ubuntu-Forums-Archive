---
title: "Screen resolution issue"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by Xoanan on 2008-04-20
Hi all

I am having a little problem with screen resolution on my mother's pc;  the screen is pushed over to the left.  I can work around it, but the monitor does not appear to have any controls for adjusting the horizontal and the vertical. 

The monitor is a flat panel and its attached to the machine itself.  There' s no brand name on this one as it was a refurbished that we bought.

[ATTACH]66509[/ATTACH]

I attempted to change it under screens and graphics, with a secondary screen, but that option is grayed out.  She is using a an i810e graphics card.

Oh yeah, the cat didn't do anything to it.  He just wanted to be in the picture.:)

Any ideas?:popcorn:

---

### Post by Vermind on 2008-04-20
Hello,
it would be more useful if You press printscreen and get a screenshot of the situation.
I can guess that You might be using a resolution that's not good for the monitor. What does xrandr say? how about ```
xrandr -s 0
``` or ```
xrandr -s 1
``` or so? 
Also, if Your /etc/X11/xorg.conf has wrong refresh and sync values for the monitor, that might cause this. Try ```
 sudo dpkg-reconfigure xserver-xorg
``` to fix the config, then restart X with ctrl-alt-backspace.

---

### Post by Xoanan on 2008-04-20
Thanx, I changed it to an attachment.   I am posting this from my own pc;  I didn't have time to do it on hers last night

Sorry

---

