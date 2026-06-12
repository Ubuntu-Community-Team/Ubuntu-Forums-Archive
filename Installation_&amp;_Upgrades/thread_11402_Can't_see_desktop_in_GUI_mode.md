---
title: "Can't see desktop in GUI mode"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by tleroy on 2005-01-16
Hi,

I installed Ubuntu Linux on a Compaq Proliant 6500 Server (old but functional, future web server), and the install appeared to go fine.  After the last rebot, when it's supposed to take me into GUI mode, the screen is blank.  If I type in my name and password, I see hard drive activity making me think it's logging me in.  I think it's just a problem with the resolution or something.  Is there a way to get it to boot into text mode and a way to change the resolution or check the graphics drivers?

Sincerely,

---

### Post by Rancoras on 2005-01-16
What video card does it use?

---

### Post by tleroy on 2005-01-16
It's an ATI Rage IIc Video Card.

---

### Post by Rancoras on 2005-01-16
You could try booting into rescue mode.  Once there check the monitor settings in your X config file to see that the settings match the manufacturer specs for your monitor.

---

### Post by tleroy on 2005-01-16
Thanks Rancaros.  I was in rescue mode, but didn't know what to do in there, even after typing help at the prompt.  :)

---

### Post by Rancoras on 2005-01-17
I did this thread a while back, see if what helped that guy helps you.

[http://ubuntuforums.org/showthread.php?t=8667](http://ubuntuforums.org/showthread.php?t=8667)

---

### Post by tleroy on 2005-01-25
These are all very helpful, but I'm afraid I may not have enough video memory?  When I run xf86config from /usr/bin/X11, it gets almost through the configuration program, then gives me an error about not enough memory selected.  It's an ATI Rage IIc, with 8 MB of ram.

---

