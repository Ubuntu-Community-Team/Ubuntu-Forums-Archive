---
title: "automatically load WLAN drivers"
date: 2009-01-14
forum: Hardware
---

### Post by athrpf on 2009-01-14
Hey everyone, 

I use a laptop with madwifi for my atheros WLAN card. It works fine except that the module is not loaded automatically at startup, but I always have to load it manually with 

sudo modprobe ath_pci

There must be a way to automate that. Can anyone help?

Thanks alot!

---

### Post by Piro24 on 2009-01-14
No problem :)

Open up /etc/rc.local with a text editor (make sure you have root priveleges!) and add 
 "modprobe ath_pci" to the start of the file.

The script is run automatically as root every time you start a session, so this should fix your problem.

---

