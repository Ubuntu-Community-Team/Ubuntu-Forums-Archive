---
title: "light blue desktop after screen settings change"
date: 2008-11-06
forum: General Help
---

### Post by jeanpaulsartre on 2008-11-06
I installed Xubuntu 8.04 on system for my dad, and he was disappointed that his screen saver wasn't working. I've figured out that I need to change the settings with the gnome power management, but not before I screwed everything up.

Before I investigated the gnome fix, I coached my dad--over the phone--to change some of the display settings. That was a bad idea.

Now, after he logs in with the xfce sesssion chooser, he only gets a light blue screen with no panels, icons, nothing. Just a pointer that moves with the mouse. The only session that works is to start a failsafe session with a terminal window that appears in the blue screen. I can get some applications to run using the terminal window--like firefox, for example--and they work fine, but they are all controlled through terminal, and I am too dumb to know how to open the display settings dialog window in order to see if I can reset whatever he changed in order to get the system back to normal.

A discussion here ([http://ubuntuforums.org/showthread.php?t=450608](http://ubuntuforums.org/showthread.php?t=450608)) suggested it is a memory problem. It is not a memory problem. Like I said, firefox runs fine. 

Any ideas?

---

### Post by john.nicholls on 2008-11-07
To get the components of Xfce working, use Alt-F2 to open a terminal and type xfwm4 (window manager), xfce4-panel (panels), and xfdesktop (desktop). After they are all showing, save the settings by going to the Settings Manager, select Sessions and Startup, and tick Automatically save session on logout.

---

