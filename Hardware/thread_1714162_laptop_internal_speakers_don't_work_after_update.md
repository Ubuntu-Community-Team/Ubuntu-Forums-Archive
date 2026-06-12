---
title: "laptop internal speakers don't work after update"
date: 2011-03-25
forum: Hardware
---

### Post by vapor216 on 2011-03-25
Hi.

My laptop model is Asus g53jw.  Using 64 bit Ubuntu 10.10

The sound did work just fine yesterday and now it does not.  The only changes I'm aware of is an update and installation of packages thru synaptic.  The headphones jack still works but there's no sound from the speakers.

I tried the suggestions here and it didn't solve my issue:
[http://ubuntuforums.org/showthread.php?t=1655069](http://ubuntuforums.org/showthread.php?t=1655069)

This is my alsa info:
[http://www.alsa-project.org/db/?f=3f45c641f9157dd78557284203a807201d447c03](http://www.alsa-project.org/db/?f=3f45c641f9157dd78557284203a807201d447c03)

Not sure if it's related to the problem, when I noticed sound was not working and started looking I found that my user was not in the audio group.  My user was also not in the video group as well as a few other groups that I'm almost certain that my user was in before.

This is from my synaptic history today:

> Commit Log for Thu Mar 24 09:22:50 2011
dbus (1.4.0-0ubuntu1.1) to 1.4.0-0ubuntu1.2
dbus-x11 (1.4.0-0ubuntu1.1) to 1.4.0-0ubuntu1.2
gnome-screensaver (2.30.0-1ubuntu1) to 2.30.0-1ubuntu1.1
libdbus-1-3 (1.4.0-0ubuntu1.1) to 1.4.0-0ubuntu1.2
libsyncdaemon-1.0-1 (1.4.5-0ubuntu1) to 1.4.6-0ubuntu2
linux-firmware (1.38.4) to 1.38.5
python-ubuntuone-client (1.4.5-0ubuntu1) to 1.4.6-0ubuntu2
software-center (3.0.7) to 3.0.8
transmission (2.04-0ubuntu2) to 2.05-0ubuntu0.2
transmission-cli (2.04-0ubuntu2) to 2.05-0ubuntu0.2
transmission-common (2.04-0ubuntu2) to 2.05-0ubuntu0.2
transmission-gtk (2.04-0ubuntu2) to 2.05-0ubuntu0.2
ubuntuone-client (1.4.5-0ubuntu1) to 1.4.6-0ubuntu2
ubuntuone-client-gnome (1.4.5-0ubuntu1) to 1.4.6-0ubuntu2


> Commit Log for Thu Mar 24 16:23:27 2011
Installed the following packages:
libdiscid0 (0.2.2-1)
libmusicbrainz3-6 (3.0.2-2)
sound-juicer (2.31.6-0ubuntu2)


** I noticed a problem at this point

> Commit Log for Thu Mar 24 21:45:58 2011
Upgraded the following packages:
libpulse-browse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
libpulse-mainloop-glib0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
libpulse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-esound-compat (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-module-bluetooth (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-module-gconf (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-module-x11 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-module-zeroconf (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1
pulseaudio-utils (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22-0ubuntu1


> Commit Log for Thu Mar 24 21:49:05 2011
Completely removed the following packages:
linux-alsa-driver-modules-2.6.35-28-generic


** I used the command line to install linux-alsa-driver-modules and removed it when it did not fix my issue.


Any ideas how I can fix this?  Please help!  Thanks.

---

### Post by vapor216 on 2011-03-25
This morning I booted my laptop into Ubuntu and now the speakers are working fine!  I don't understand the nature of this problem... I powered the laptop off rather than rebooting, that was a difference.  I know it was specific to my Ubuntu installation because I tested the speakers to work fine in Windows while they were not working in Ubuntu.

Another strange thing occurred, not sure if it is related to the speakers.  While I was using the terminal, compiling something, the text in the terminal changed from white to light blue and I noticed that all the "foreground" text changed color as well, like in menus of my windows and the text under the icons on my desktop.  It all changed from white to light blue and then after a couple minutes, it changed back to white.  And when I hovered the pointer over the blue text of the desktop icons, they changed back to white.  Weird!

So far today everything seems fine but I'm left wondering, is my installation broken some how?  Should I re-install packages?

---

### Post by cutgah on 2011-04-11
lol, had the same problem, same computer and the same solution. NOT restart, but shut down :P

---

