---
title: "keyboard/mouse/network broken - HELP!"
date: 2009-04-19
forum: Hardware
---

### Post by clconway on 2009-04-19
After a reboot, my laptop keyboard and mouse refuse to respond at the GNOME login screen, except for Ctrl-Alt-Delete, Ctrl-Alt-F1, etc. The keyboard works fine in a text terminal (Ctrl-Alt-F1, etc.).

If I plug in a USB mouse or keyboard, they work fine too and I can login to GNOME. But Network Manager says "no network devices available."

I suspect this has something to do with an attempted PulseAudio upgrade from a backported package, but I'm not exactly sure what. I'm also completely at a loss as to how to back out of the upgrade it I can't connect to a repository.

I'm running Intrepid. Here are some of the packages I've upgraded recently (don't recall the last time I rebooted):

From a PPA:
pulseaudio 0.9.15

Backported from a Jaunty:
udev 141-1
libasound2 1.0.19
libcanberra 0.12

Upgraded from the official repos:
cups 1.3.9
libpoppler3 0.8.7
libc6 2.8-20080505
gvfs 1.0.2
nvidia-glx-180 180.11

---

### Post by clconway on 2009-04-20
I "fixed" this by upgrading to Jaunty using the Alternate CD. The dist-upgrade blew away whatever was causing the problem.

---

### Post by lrkwz on 2009-04-21
Same problem.
I've fixed keyboard/mouse in the login screen adding

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        **Option          "AllowEmptyInput" "off"**
EndSection

```

in /etc/X11/xorg.conf file.

I have no real solution for networking (I've hand configured it but firefox starts offline, empathy does not connect at all ...:() and sound :(:(

My workaround for networking is: install [wicd]("http://wicd.net/download.php")

---

