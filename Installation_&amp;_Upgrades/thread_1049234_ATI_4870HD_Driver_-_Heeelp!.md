---
title: "ATI 4870HD Driver - Heeelp!"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Zhoth on 2009-01-24
Hello!

I've tried many times now to install the driver (and Ubuntu...closing in on 20 times) from the ATI-homepage, but I just can't get it to work. I've put up a similar post in the Swedish Ubuntu forum, but no reply so far... (9,5 million citizens and 3 Linux users...so what can I expect ;) ).


Hardware/Software:
Ubuntu ver 8.04 (Clean install...nothing added...NOTHING)
ATI 4870HD Gfx-card
Samsung 244T monitor (1920x1200 Widescreen)

Can anyone, guru or not, create a 'What do to' (if anything) to get it to work? Step by step (for a complete Linux-idiot to follow). I mean very very basic like:
A: Install Ubuntu 8.04.
B. Start Ubuntu.
C: Login...
You get the picture. Anything technical like "first you need to | the xx23promtisblabla" I WILL NOT UNDERSTAND! If I must do something BEFORE I try to install the driver...take that in account. Where/how and when...reboot or no reboot...and so on. You're talking to a complete ubernoob that wants to try Linux but cannot get past a 'black screen' OR running it at 800x600 on my 24" monitor...and thats just bad..very bad.

Thank you :)

/M

---

### Post by llamabr on 2009-01-24
First, you might just try installing 8.10.  Next, rather than messing with the driver, try:

sudo dpkg-reconfigure -phigh xserver-xorg

Sometimes it doesn't get the resolution right during install, and needs reconfiguring.

---

### Post by Zhoth on 2009-01-24
I get:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090124172230

And nothing happens..no 'reboot now' window, no new resolutions to choose from...nothing



8.10 for me is:
A: No network (though I know how to fix it...sort of).
B: Black-screen upon reboot. It just doesn't work at all.

---

### Post by khelben1979 on 2009-01-24
I would guess that your xorg.conf has been corrupted.

Share what you have in the /etc/X11/xorg.conf file by attaching it to this thread.

sudo root
cp /etc/X11/xorg.conf /tmp or another catalog which suits you.

then change it's file attributes so that you as a normal user can attach this file to this forum by using the chmown command:

chown kalle.kalle /tmp/xorg.conf (replace kalle to your username)

If the above is too complicated, you should probably start all over again and try install Ubuntu from scratch and skip messing around with the ATi driver from the ATi homepage and only install packages which comes directly from Ubuntu.

I myself have hassled with Ubuntu last year and I didn't like it one bit. Go for Debian instead.

By the way, I'm a swede too. :popcorn:

---

### Post by Zhoth on 2009-01-24
I have a clean install now...nothing added or installed...havn't tried to install any drivers. I just started it as it was/is.

But, as I said in the first post. There _must_ be some way to install the darn thing? (Step by step). Im stuck at the 'Ok...Im logged in...now what?' state. EVERYTHING is "greek" for me in Linux. I don't know what anything is, what it does.... sort of..like if you gave a man (or woman) from the stone-age a computer... that's the Linux-knowledge I have.

Some sort of autoupdate-to-the-latest-driver-program-thingie or a 'Would you like to install a driver?' program/option would be nice...so noobs like me could actually see what the h.. we are doing (and what is happening behind the text that's scrolling what seems to be random letters and numbers).


Been thinking about other dists (?), but since Ubuntu can be "Installed within windows", I can actually start windows after Linux fails to work (like all of the time) and remove the thing and still have a working OS (Windows) without having to reinstall the computer at every failed attempt.

/cry

---

