---
title: "Monitor resolution"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by mjt_colo on 2009-04-15
This may sound like a simple problem to you, but to me it is way beyond my Linux/Ubuntu skills.

I had an older HP desktop in the garage and a Sony Multiscan100ES monitor so I installed Desktop Ubuntu 8.10 thinking it would all just work.  Well mostly, except the highest resolution is only 800x600 and when I open a terminal window it just opens a blank white rectangle that I can't see anything in when I type. I can type in xterm and get a smaller window that I can see.  But the monitor is not working well.

The xorg.conf file basically just a shell.  No actual info in it where I would expect to see a file that is like the one on my laptop running 8.10.

Help would be appreciated!!!!

---

### Post by Pasdar on 2009-04-15
Did you get a notification about installing proprietary drivers? Or did you install any drivers at all?

Click on System > Administration > Hardware Drivers, if you see anything click on the latest and install.

What videocard do you have?

---

### Post by mjt_colo on 2009-04-15
no there are no drivers in that location and it didn't install any.  I think it is an intel videocard

Mike

---

### Post by Pasdar on 2009-04-15
Type lspci in terminal, that should tell us what video card you have.

---

### Post by mjt_colo on 2009-04-15
lspci says:
Intel 82810E DC-133.

---

### Post by Pasdar on 2009-04-15
press CNTRL + ALT + F1, you will go into terminal if you do that, and then type:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by mjt_colo on 2009-04-15
well the terminal window is just white space, so that doesn't work.  But xterm does and when I entered that command and then logged out and back on, there was no change.....  sadly

---

### Post by Pasdar on 2009-04-15
Not the terminal window, write down the command that I wrote. when you press CTRL, ALT, F1 it leaves the graphical environment and enters a black terminal environment. It'll ask you for your login and password, enter it... then enter the command.reboot after that.

---

### Post by mjt_colo on 2009-04-15
Actually it didn't give me a terminal window or ask me for my username or password.  It just blanked the screen for a few seconds and then showed me what was there before.  That is why I put your previous command in the xterm window and rebooted after that.

---

### Post by Pasdar on 2009-04-16
You have a very strange problem, how about you disable the visual effects... if you've enabled it:
System->Preferences->Appearance, "Visual Effects" tabs, and select "none"

---

### Post by mjt_colo on 2009-04-17
I did get the monitor to work ok, but still cannot get the resolution beyond 800x600.  I would love to run in 1024x768 mode.  The monitor is a Sony multiscan100ES.  

thanks for your help

---

