---
title: "Howto: Thinkpad x60"
date: 2009-08-15
forum: Hardware
---

### Post by MikeEcho on 2009-08-15
I've just got my X60 working: By working, I mean I have the rotate button working with the digitizer. For me, this was a convoluted progress, and required about a day of sifting through forums online. Thus, I have decided that I should post the steps I took to achieve such a result, both as a reference for others, as well as for me, should I ever need it! As I discover more with this machine, I hope to update this thread (Even better would be if some other kind souls could contribute!).

[SIZE=3]**From a clean install of Jaunty-**[/SIZE]

[SIZE=3]*Getting the tablet recognised:*[/SIZE]

[This thread]("http://ubuntuforums.org/showthread.php?t=1038949") details how to install the linuxwacom drivers. I followed it until the end of Section 1.

From here, I reinstalled the previously purged packages:

```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
```

Further to this, I followed the directions in [this blog post]("http://blog.aliencam.net/2009/06/ubuntu-setup-guide-viii-wacom-tablet-config/").

This meant that the basic tablet features were now recognised and enabled.

*[SIZE=3]Rotating screen:[/SIZE]*

Now that the tablet identifed itself correctly, it was able to receive xsetwacom commands, and find a [rotating script]("http://luke.no-ip.org/x60tablet/#rotate_script"), to rotate and align the screen and tablet for portrait writing. I chose this script as it also aligns the directional buttons on the tablet bezel.

[SIZE=3]*To Do:*[/SIZE]
Enabling right click/ the eraser with the stylus (for now, I have enabled simulated secondary click under mouse preferences).

Automatic rotation of the screen when the device is converted into tablet mode.

Fingerprint Reader (thinkfinger is having file writing issues at the moment, which I don't seem to be able to fix).

Anyway, I hope what little I have can be of some use to someone, and saves them having to trawl through everything like I did.

---

