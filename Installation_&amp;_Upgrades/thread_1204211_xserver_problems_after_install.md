---
title: "xserver problems after install"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by rophl on 2009-07-04
just installed 9.04 and got an error from x.

worked fine when booting from the CD, but now that it's installed properly it returns the error
"[FONT=Courier New]Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

"[/FONT][FONT=Courier New]Warning: Failsafe mode was already attempted within 30 seconds
Warning: Falling back to gdm to report the issue[/FONT].
^Y"

"[FONT=Courier New]The x server is now disabled.  Restart GDM when it is configured correctly."

I guess it's a problem with an unrecognised graphics card so I stop the gdm, then put in "sudo dpkg-reconfigure xserver-xorg" to try and change some settings, but the prompt stops early, kicking me back into the terminal after setting the keyboard options with the message:

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.cong.20090704164206"

I'm confused, anyone got any ideas?
[/FONT]

---

### Post by rophl on 2009-07-04
hmm, rebooted a couple of times, it worked on the third try. it would still be nice to know what caused this

---

### Post by synapsys on 2009-07-04
It sounds like ubuntu tried to automagically set up your graphics card and failed at doing so. The best thing to do is what you did, and then once you've booted, install your graphics card drivers.

---

### Post by rophl on 2009-07-04
that's the thing though, what I did didn't do what I did think it would do. (sorry). the reconfigure died after setting up the keyboard and didn't let me get through to setting up the display

---

