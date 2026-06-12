---
title: "Fresh Install Questions (Solved)"
date: 2005-12-01
forum: General Help
---

### Post by chakra_dude on 2005-12-01
Good day to all. I just had installed Breezy 5.10 last night. I opted to overwrite my Hoary 5.04 installation, using the same procedure as i did when i installed Hoary. Everything went well but after the installation process, the fressh install booted, initialized, and stopped. I mean the monitor when blank like in a stand-by mode. When i pressed the power button(i assumed at first that it was in stand-by mode)this appeared:

Breezy 5.10
ubuntu login:

I tried typing my login and pressed enter, and after a few seconds, my machine shut down, as in a normal state. I tried rebooting but the same thing happened. I tried again to reboot to XP but no problems. Tried Hoary again, but the same thing happened.

I'm puzzled. What did I miss? I posted this thread to gather some points before I will reinstall my Breezy tonight.

Thanks in advance to all expert minds who will enlighten me.

Cheers!
TOTO :)

---

### Post by aysiu on 2005-12-01
Instead of pressing the power button, try pressing Control-Alt-F1.
A DOS-like command screen should appear.
Log in and type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chakra_dude on 2005-12-01
Thanks bro. Is this normal? I haven't encountered this one when I was installing Hoary 5.04

---

### Post by aysiu on 2005-12-02
[QUOTE=chakra_dude]Is this normal?[/QUOTE] No. It happens when Ubuntu guesses (or you say explicitly) that your screen resolution is higher than can really be supported by your monitor / video card.

---

