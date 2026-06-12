---
title: "A Few Lenovo T60p Problems"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by akimatsu123 on 2008-03-26
Hi, 

I have several problems running Ubuntu. I love the OS, and i really wish i could get it fixed. 

First of all, i cannot suspend or hibernate. When i click on those options, the screen just simply turns black, then the suspend light flashes (for windows when i go into standby, the light simply turns on and doesnt flash). I don't get an error warning, or anything. I can't bring it back after that, and i have to force shutdown. How can i fix this problem?

Secondly, my laptop seems to be extremely hot. I had similar problems in windows, but it wasn't anywhere near as severe. I heard my friend say it's got something to do with Windows knowing when to use the CPU up to full, and when to take a break, but Ubuntu always cranking the CPU up to maximum. Is this true? Is there a way i can change that?

Thanks,

---

### Post by tastatur on 2008-03-26
1. Most of laptop user here have problem with Suspend /Hibernate on Ubuntu. You can use search feature on this forum to know which reason causes your problem (such as Kernel, Video Driver..etc)
New version of Ubuntu (Hardy) will be released in next month. Now you can test its beta version. I hope that Suspend/ Hibernate works better in this new version.

2. You need "program" to manage your CPU-Frequency Scale (We assume that you use Ubuntu 7.10 with Gnome)
. Open Terminal and run this command:
```
sudo dpkg-reconfigure gnome-applets
```
say yes to install scale-manager

. Right Mouseclick on your panel (taskbar), choose add to Panel to add new applet
Category: System & Hardware
Applet Name: CPU Frequency Scaling Monitor

. Left Mouseclick onto your new applet, you can choose some configuration for your CPU now (such as Conservative, Ondemand, Performance or Powersave)

Goodluck! :popcorn:

---

### Post by akimatsu123 on 2008-03-26
thanks,

i just got the applet. it seems great. i'll test it out. i also bought a table fan today so combined with the new applet, it should sove the problem. 

thanks again for your help

---

