---
title: "[SOLVED] Easy dual monitor setup - where?"
date: 2008-11-28
forum: General Help
---

### Post by kcredden on 2008-11-28
Hey folks: Please don't yell, as it's probably been talked to death. But when I first got on Ubuntu, I found a page somewhere that showed me how to set up a dual monitor, very, very easly. I didn't have to back up my xorg file, or do anything though the command line. It was like I installed a driver or program, ran it, answered a few questions, and it worked. It also allowed the 2 seperate monitor/desktops that I normally use in Windows 2k

For the life of me, I can't find that anywhere, not even sure if it was here or not. The search isn't showing me anything that looks like it either.

So have you got any ideas? My specs are below. 

nVidia Geforce 7300 dual monitor, w/an lcd, and crt monitors.
Intel p4 3ghz
1g memory
Asus motherboard
Kubuntu 8.04.1 w/KDE 4 (but running normally in KDE 3.x)

- Kc

---

### Post by amiller2571 on 2008-11-28
I have never tried setting up a dual monitor on Ubuntu, but this may help you. 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

I don't know what type of video card you have but if it's Nvidia here you go.

---

### Post by Usufruct on 2008-11-28
The easiest way I've found to get them working with an nVidia card & driver is by using the nVidia X Server Configuration app.  If you don't already have it, install it by running from the terminal:

```
sudo apt-get install nvidia-settings
```

This makes it very easy to change all kinds of display settings, including multiple monitors.

---

### Post by chinsaw on 2008-12-13
I am having a very simular problem.  I am running a Nvidia GeForce 8800 GTS card with an Acer AL2216W and a Samsung SyncMaster.

I Have the NVIDIA X Server Configuration app.

When I go to the NVIDIA program the acer screen shows up under DFP-1.  When you click it the information shown is all unknow. So I went in and enabled the Acer screen saved the changes.  Then I restarted the computer. When the computer came back up still no Acer Monitor.

How can I fix this issue?  Please be Gentle I just installed the Kubuntu Linux last night, and this is all new to me.

---

