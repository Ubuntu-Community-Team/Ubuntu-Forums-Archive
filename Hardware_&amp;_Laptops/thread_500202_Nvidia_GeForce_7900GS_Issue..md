---
title: "Nvidia GeForce 7900GS Issue."
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by infinitezero on 2007-07-13
Has anyone with this config: Asus P5B deluxe, 4 GB memory, XFX GeForce 7900GS or at least the GeForce 7900GS video card been successful at getting the Nvidia driver installed? If so what method did you use and what version are you running.

Thanks,
iz

---

### Post by bdtgp on 2007-07-13
I don't have that set up but I have an ABIT board with a GeForce 7300gt.  Heres what I did:
```
sudo apt-get install nvidia-glx-new
```
Then
```
sudo nvidia-xconfig --no-composite
```
Then
```
sudo gedit /etc/usr/share/applications/NVIDIA-Settings.desktop
```
Add this to the file that pops up:
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```
Save that file and then exit and it should go back to your terminal.  Now just log out and hit Ctrl+Alt+BkSp to restart the X Server.  That should work.

---

### Post by infinitezero on 2007-07-13
I will give that a try. Are you running 7.04?

Thanks,
iz

---

### Post by dabl on 2007-07-13
I've used both bdtgp's method and also (more recently) the Envy installer from Alberto Milone's web site.  My mobo is an Intel, so if you can't get it to work, the issue is probably a mobo/BIOS thing, not a GeF 7900 GS thing.

---

### Post by infinitezero on 2007-07-13
Is there a work around for the bios?


Thanks,
iz

---

### Post by dabl on 2007-07-13
> **infinitezero said:**
> Is there a work around for the bios?

I have no clue, but I'd Google on "Asus P5B Linux" and "Asus P5B video" and stuff like that -- probably you are not the first to hit this.  There may be some setting in BIOS related to your PCI bus that needs changed or turned off -- you get into your BIOS settings from whatever the Asus mobo message is at boot ... "F1 for settings" or something like that is usually what you see fly by when you first boot your PC. You have to hit it fast.

---

### Post by LeGollemux on 2007-07-15
Hi there,

Thanks for the help. The whole /etc/usr thing threw for a bit but as soon as I worked it out I got the card working just fine. Im running Ubuntu Feisty Fawn on an ASUS F3JC Series with 1gig of RAM and an NVIDIA Go 7300 display. Everything works just great, wireless networking the works.

Thanks again for the help!

---

### Post by lolzlolz on 2008-01-02
dabl did u previously have a 7900gs because i do and im having trouble as well but i think i can fix it while others say that it doesn't support the xserver at all

---

