---
title: "can't seem to install nvidia drivers for my 7300gs"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by ninjapig on 2009-08-09
This is really disappointing. I just installed 9.04 on my pc and tried 

owner@owner-desktop:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)



There doesn't seem to be anyway i can activate my nvidia card so it's hardware supported. can someone help me out...it's really irritating that ubuntu can't handle this by default as i hoped.

---

### Post by presence1960 on 2009-08-09
Go to Synaptic Package Manager and install envyng-core and envyng-qt. or install through terminal ```
sudo apt-get install <package name>
```

Then use the Envyng software to install your Nvidia drivers.

P.S. Did you check System > Administration > Hardware Drivers to see if your Nvidia driver is there? if it isn't use Envyng

---

### Post by wojox on 2009-08-09
This always helps me :
```
https://help.ubuntu.com/community/NvidiaManual
```

---

