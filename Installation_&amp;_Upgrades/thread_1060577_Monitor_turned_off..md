---
title: "Monitor turned off."
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-02-04
Hi,

I just installed Ubuntu 8.10 on a Thinkpad X200 laptop. Once I logged into the desktop, I tried to configure the monitor resolution. In the resolution list, I chosed "Off". Then the screen restarted, and I can no longer see anything. I can only enter the username and password, and then see a black screen.

I am looking forward to getting my monitor back to work. Hope someone could help me on this problem. Thank you.

---

### Post by huruixd on 2009-02-04
Help me pass through this.

---

### Post by networm1230 on 2009-02-04
> **huruixd said:**
> Help me pass through this.

hello! I do not own a laptop and never did. I am a desktop PC user. I am going out of my desktop PC world and go laptops. will what i know about laptops when the screen gos black.

possible tips to help you.

1. start the laptop from a cold boot. a cold boot is when a computer is started up from a powerless state.

2. change you resolution to a lower res

3. try a different power scheme 

4. tack out the laptop battery and put it back in mack shore the battery is charged all the way before installing.

5. use the power cable to the wall plug in wan in use if possible

---

### Post by bukwirm on 2009-02-04
Press Ctrl-Alt-F1, enter your username and password - this should log you into a terminal. Then you can edit your xorg.conf file with a command-line text editor such as nano.

---

### Post by huruixd on 2009-02-05
The version of Ubuntu on my laptop is 8.10. Is it still possible to edit the /etc/X11/xorg.conf file to get my monitor work?

And how to edit the xorg.conf file?

---

### Post by bukwirm on 2009-02-05
Sorry about my earlier advice - this might be better:

First, [this article]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") has hints on restoring Gnome to it's default settings - this might fix your problem.

If that doesn't work, try running the command "sudo dpkg-reconfigure -phigh xserver-xorg" it should reconfigure X Windows back to it's default settings.

If that stuff doesn't work, let us know and I'll think of something else.

---

