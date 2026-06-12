---
title: "cannot avoid screen turning off after several minutes"
date: 2009-11-26
forum: Hardware
---

### Post by thrantir on 2009-11-26
Hi to everyone! This is my first post, forgive me for my bad English (I'm Italian :-))

I recently installed Ubuntu 9.10 on my eeepc 901 and on my girlfriend laptop, a Dell presario. Both of them turn off the screen after several minutes (I think about 5) ignoring what I set in power management options. That behaviour is really annoying watching a film

Could someone tell me how I can convince them to behave as I want?

Thanks in advance

---

### Post by jacobs444 on 2009-11-26
try also changing the screensaver settings, and make sure the power settings are still set, then reboot. If this doesn't fix, then is probably a bios problem (the bios may have its own power settings!) (the monitor can {though rare} have it's own power options built in, that require using the buttons on the front of the monitor to sort out!. GOOOOOOOD LUCK!

---

### Post by thrantir on 2009-11-26
I cannot remember now if I already followed this way, but I'll try asap

Googling about this issue it seems it could be a regression of ubuntu 9.10 (in 9.04 I hadn't the problem)

I think this issue isn't related to BIOS setting as it appeared on two completely different laptops just on updating to ubuntu 9.10

---

### Post by Grenage on 2009-11-26
I also experienced this after upgrading 9.04 to 9.10; the screensaver is not blocked and the mouse cursor does not fade when a film is playing.

I haven't spent any time working out why, because I plan on performing a fresh install.  What I _do_ know is that I had to set my screensaver to it's max setting.

---

### Post by thrantir on 2009-11-26
the installation on my eeepc was from scratch, while the one on the dell was an update from 9.04, but that porblem came anyway

---

### Post by Grenage on 2009-11-26
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884)

We aren't alone, some things were changed; stay tuned!

---

### Post by thrantir on 2009-11-26
that thread is very interesting!

maybe a temporary solution is a script like this:

```
#!/bin/bash

while true
    do
        xset dpms force on
        sleep 300
    done

```

---

### Post by thrantir on 2009-11-30
this method doesn't work :-(

I'll try this asap:

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
```

and

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool true
```

---

