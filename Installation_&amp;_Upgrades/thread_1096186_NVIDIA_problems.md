---
title: "NVIDIA problems"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by comradejanus on 2009-03-14
Hello, 

Thought id finally register as I had done everything that had been suggested for others who had the same problem, and still no lock.

I have finally got around to installing ubuntu 8.10 today, and I really love it except for the agony in trying to install the newest NVIDIA drivers so that I can play some of my fps games.

I tried using ENVY but that didnt work. I tried manually installing and using the first feature but I get the following message "There was an error in the installation process. You can see the log file /var/log/envy-installer.log" - I don't know how to open that. When I enter it in the terminal I get access denied.

Well anyway, I downloaded the the drivers from the NVIDIA website, as well as several others. The main one I tried was "NVIDIA-Linux-x86-100.14.09-pkg1.run". I tried running it by pressing "ctrl-alt-F1" and then disabling the GNOME and running the driver. The installation processes runs fine and it downloads a new kernel and such. The installation process ends and GNOME tries to restart but it but theres anouther error and goes into low graphics mode and im asked if I want to return to an earlier configuration. When I finally return to GNOME ther resolution is horribly low until I restart.

Any clues anyone? Much appreciate any help.

---

### Post by tommcd on 2009-03-14
What nvidia card do you have? Unless you have some specific reason for needing the driver from nvidia.com, it is much easier and better to use the driver from the Ubuntu repos.
Just go to: system > administration > hardware drivers and see if you can enable the card.
Or if you have a fairly recent nvidia card, just open a terminal and run:
```
sudo apt-get install nvidia-glx-180
```
Run:
```
aptitude show nvidia-glx-180
``` 
to see what nvidia cards the 180 driver supports.
You may need to run:
> sudo nvidia-xconfig
to enable the driver. You can also run:
> sudo nvidia-settings
to access the settings menu.
Please completely remove the driver from nvidia.com before you install the driver from the Ubuntu repos.

And welcome to the Ubuntu forums!

---

### Post by comradejanus on 2009-03-14
Thanks so much for the welcome and replying so quickly!

Knew I'd forgotten to mention something. My graphics card is an NVIDIA 8300 gs.

I tried using the graphics card driver on system > administration > hardware drivers and used driver version 177 (recommened), but games seem to run waaaay more choppy than they did before on vista leading me to think the driver aint configured properly.

I will try running the code you mentioned, but just to check how do I ensure the driver is removed? Sorry I'm a complete noob I only starting using Linux for the first time in my life today.

---

### Post by tommcd on 2009-03-14
> **comradejanus said:**
> 
I will try running the code you mentioned, but just to check how do I ensure the driver is removed? Sorry I'm a complete noob I only starting using Linux for the first time in my life today.
To remove the 177 driver from the Ubuntu repos. Hit ctl + alt + F2, then run:
```
sudo /etc/init.d/gdm stop
```
this will stop X.
```
sudo apt-get remove --purge nvidia-glx-177

```
this purges the 177 driver.
```

sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```
this will install and configure the 180 driver.
then ctl + alt + F7 to get back to the desktop.
If you need to uninstall the driver from nvidia.com, run:
```
sudo sh NVIDIA-xxx.run --uninstall
```
[http://us.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-04-section-04.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-04-section-04.html)
make sure X is stopped as outlined above first.
It always a good idea to backup you current xorg.conf before installing drivers, so do this first before you do anything:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by tommcd on 2009-03-14
> **comradejanus said:**
> 
Knew I'd forgotten to mention something. My graphics card is an NVIDIA 8300 gs.


The nvidia 8300 GS is listed as supported by both the 177 and 180 driver.  If I was getting less than adequate performance with the 177 driver then I would try 180. You could always go back to 177 if you want.
Run:
> glxinfo | grep -i direct
 to see if direct rendering is enabled. It should output: "direct rendering: Yes"

---

### Post by comradejanus on 2009-03-14
It works! Thanks so much! I've spent hours on that today!

The driver is working but some of my games that I run with wine still run really choppy. I think I haven't got the game configured properly or something.

Thanks again for the help.

---

### Post by tommcd on 2009-03-15
> **comradejanus said:**
> 
The driver is working but some of my games that I run with wine still run really choppy. I think I haven't got the game configured properly or something.


Running games through Wine is an imperfect solution at best; and likely to be problematic. Try some native linux games like Nexuiz or Sauerbraten (both are in the Ubuntu repos). I would think the nvidia driver performance in native linux games would be much better.

---

