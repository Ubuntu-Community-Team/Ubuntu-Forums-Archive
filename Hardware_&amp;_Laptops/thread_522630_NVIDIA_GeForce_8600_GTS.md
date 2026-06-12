---
title: "NVIDIA GeForce 8600 GTS"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by doublementh on 2007-08-10
Does the latest version of the distro have drivers for this card?

I'm new to the command line, so, I'm not really up for installing the drivers until I get to know it better.

---

### Post by fredj on 2007-08-10
Probably not but Nvidia also produce their own Linux driver and I imagine that the latest version
would support it. Look on their website. Nvidia have been very good at supporting Linux for
a long time now.
Installing their driver through the command line is not that difficult and you will be
able to get help here since it is something that many of us are familiar with.

---

### Post by Prodigious Penguin on 2007-08-16
The latest nvidia driver in the Ubuntu repositories didn't support my GeForce 8600, so I am trying a driver direct from nvidia.  Here's the link to their driver page:
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

---

### Post by rrinker on 2007-08-16
Look at posts 11, 19, and 26 in this thread.

[http://ubuntuforums.org/showthread.php?t=453942&highlight=8600+gts]("http://ubuntuforums.org/showthread.php?t=453942&highlight=8600+gts")

 I was able to get my MSI 8600 GTS working in Fiesty by basically following these various steps. First I uninstalled anything nvidia related in Synaptics. I downloaded the latest drive from the nvidia site. Hit ctrl-alt-f1 to change to the first text console, used sudo /etc/init.d/gdm stop to stop Gnome, then ran the nvidia installer.

 Failing that you can restart in console only mode and install the nvidia driver from there, although you have to switch to runlevel 3, the driver does not want to be installed as runlevel 1.

 The install did everything for me - including putting the correct settings in my xorg.conf file, I just restarted after installing and now I had nice fast OpenGL performance.

---

### Post by FuturePilot on 2007-08-16
I have an 8400 and the driver in the repos didn't work. So I'm guessing the 8600 won't work either. It wasn't detected by the Restricted Manager either. I had to use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to get the driver working. You might want to give that a shot.

---

### Post by Prodigious Penguin on 2007-08-16
I will second with rrinker, the nvidia installer from the website got everything working for me.  For the record, my exact card model is Asus EN8600GT.

---

### Post by rojanu on 2007-08-19
The NVidia installer worked for me to but for some reason machine will hang when I either reboot/shutdown,  it will hang after I click on the button with mouse still moving but no keyboard response, After a cold restart, I have to rebuild the modules using the installer again!!!!

Any  ideas??

---

### Post by tseliot on 2007-08-19
> **rojanu said:**
> The NVidia installer worked for me to but for some reason machine will hang when I either reboot/shutdown,  it will hang after I click on the button with mouse still moving but no keyboard response, After a cold restart, I have to rebuild the modules using the installer again!!!!

Any  ideas??

If you want a quick (but unsupported) way to solve your problem you can follow these steps:
Download and install Envy:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```
```
sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```
```
sudo apt-get install -f
```

Then follow point B (start from step 2 of point B) of this page (**if you don't do this Envy won't work for you**):
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by rojanu on 2007-08-19
Well I can't use because it does not support gutsy, I have upgraded in a hope that it will be the cure to this problem :(

---

### Post by tseliot on 2007-08-19
> **rojanu said:**
> Well I can't use because it does not support gutsy, I have upgraded in a hope that it will be the cure to this problem :(

You can get around the problem:
[http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107)

---

