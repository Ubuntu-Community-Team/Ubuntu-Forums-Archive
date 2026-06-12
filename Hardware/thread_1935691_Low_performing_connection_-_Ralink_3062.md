---
title: "Low performing connection - Ralink 3062"
date: 2012-03-04
forum: Hardware
---

### Post by micheledm on 2012-03-04
Hello everyone. I'm having lot of troubles with my wifi card (Ralink 3062). Modules are installed correctly, blacklisted the usless drivers (rt2800pci, rt2800lib, rt2800usb, rt2x00pci, rt2x00lib, rt2x00usb) and nm connects to my wifi network.

The problem comes when loading websites: connection is slow and unreliable, often sites refuse to load or take ages (and I have got a good 10Mbit fiber optics, no troubles with Win on same PC or every other device).

My feeling is that this problem came when i updated the kernel to last version 3.0.0-16-generic. After noticing it i deleted the modules, installed back again but the problem is the same.


Do you guys have any clues how to troubleshoot the problem?

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by micheledm on 2012-03-14
Thanks for the try but my system is running with another wlan card which uses different modules than yours!

---

### Post by micheledm on 2012-03-17
Solved by upgrading to 12.04 beta which uses a new and working version of the Ralink modules

---

