---
title: "Intel Centrino Wireless-N1000 Slow on Public WiFi (ThinkPad X220)"
date: 2012-02-24
forum: Hardware
---

### Post by steevven1 on 2012-02-24
My wifi is terribly slow on all public/unencrypted networks, even with excellent signal strength and on normally very fast networks.

I have opened a bug for it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218)

Anyone else noticed this? Suggestions on what to try?

---

### Post by dEc0qa on 2012-03-11
> **steevven1 said:**
> My wifi is terribly slow on all public/unencrypted networks, even with excellent signal strength and on normally very fast networks.

I have opened a bug for it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218)

Anyone else noticed this? Suggestions on what to try?


I have the same problem in a home network using a router. Comparing with an older Intel card, it is very slow.

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

