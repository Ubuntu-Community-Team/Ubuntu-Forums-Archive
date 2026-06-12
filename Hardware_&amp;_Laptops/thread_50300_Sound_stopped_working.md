---
title: "Sound stopped working"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by ravuya on 2005-07-19
Hey,

My sound was working before, but as I booted into 5.04 today I noticed that my little speaker icon had an X icon next to it. Turning it up didn't seem to work from inside GNOME.

Here's what I've done so far:
- Killed and restarted esd (doesn't work; restarting just locks esd up and it doesn't do anything, no errors in syslog or dmesg)
- Run alsamixer; no errors given to me at all (the CENTER channel was turned off, but I unmuted it and still no dice).

I'm using the snd_via82xx driver (Realtek ALC850 on a VIA 8237). I can't see any errors in dmesg or anything, so I'm utterly confused at what's broken here, nor can I think of what I might have installed or done to have broken the sound. I haven't changed any BIOS options.

---

### Post by darkmatter on 2005-07-19
Right click the applet. Uncheck the 'mute' option. ;)

---

### Post by ravuya on 2005-07-19
[QUOTE=darkmatter]Right click the applet. Uncheck the 'mute' option. ;)[/QUOTE]

First thing I tried.

**EDIT**: D'OH! For some reason moving the little volume slider didn't work, but that did. I'm really confused now. ;)

---

### Post by darkmatter on 2005-07-19
[QUOTE=ravuya]D'OH! For some reason moving the little volume slider didn't work, but that did. I'm really confused now. ;)[/QUOTE]

Told you so. Glad to hear you have sound re-established.

---

