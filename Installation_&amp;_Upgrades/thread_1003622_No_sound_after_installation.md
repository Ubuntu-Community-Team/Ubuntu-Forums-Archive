---
title: "No sound after installation"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by AmazinAzn on 2008-12-06
I've never used an OS other than Windows and now that I have I'm glad I tried but the only problem is I have no sound at all. Not sure if this helps but here:

```
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
        Subsystem: C.P. Technology Co. Ltd Device aa08
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdbfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

### Post by Pumalite on 2008-12-06
Try to open all your repos and then try:
sudo apt get update
sudo apt-get dist-upgrade
Reboot and try your sound again.

---

### Post by AmazinAzn on 2008-12-06
Still no sound.

---

### Post by Pumalite on 2008-12-06
Turn your volumes in alsamixer to 100%

---

### Post by AmazinAzn on 2008-12-06
How do I do that? I can't seem to find it.

---

### Post by Pumalite on 2008-12-06
Go to Applications>Accessories>Terminal
On it type:
alsamixer (press 'Enter')

---

### Post by Sealbhach on 2008-12-06
Also right-click on your Volume icon in the panel and Open Volume Manager. Make sure everything is turned up. 


.

---

### Post by zobot1 on 2008-12-06
On my laptop sound plays on inside speakers only with:

$ cat /etc/modprobe.d/alsa-base |grep snd-hda-intel
options snd-hda-intel model=full_dig

---

