---
title: "[SOLVED] Intrepid Nvidia driver issue. Boots to text"
date: 2008-11-07
forum: General Help
---

### Post by mattkoehn on 2008-11-07
So it seems like people are able to get the nvidia drivers to work but I've haven't been able to. I have a Geforce 7800 which is supported by both the 177 and 173 drivers to the best of my knowledge. I'd read a couple of other people's solutions to the driver issues they'd had including purging nvidia-glx-177 and nvidia-177-kernel and then reinstalling. But no dice.

Tried just clicking on the restricted driver manager window for both drivers, purging in between. No good.

If I uninstall everything and remove the xorg.conf I am able to boot with the Mesa driver. It just seemed like people were having success with video cards similar and I am curious what the solution is. Thank you for any time you spend.

---

### Post by Peter09 on 2008-11-07
You can try booting in recovery mode and selecting the xfix option.

---

### Post by mattkoehn on 2008-11-07
Everything came out the same. This is a new install from the Intrepid ISO only a day or so old. I was trying to get it to work on an upgrade and though if I did a clean install it would work.

Thanks for the quick response.

---

### Post by dabl on 2008-11-07
At the text prompt, log in and run ```
sudo /etc/init.d/gdm stop

```
Then do the following:

1. ```
sudo apt-get install envyng-core
```

2. ```
sudo envyng -t
``` and choose #1 "Install Nvidia Driver" and on the next screen choose #0 for 177.80.

3. When you are back to the EnvyNG menu screen, exit.

4. ```
sudo nvidia-xconfig
```

5. ```
startx
```

:guitar:

---

### Post by mattkoehn on 2008-11-07
When booting straight to terminal with the nvidia driver incorrectly installed, envyng -t threw up this error. 

> TypeError:list indices must be integers

Actually there was a whole mess before it. But it looks like python is freaking out. So i uninstalled the incorrect drivers, booted with mesa to try the graphical version but got the same errors. Just wanted to give a status update.

---

### Post by Peter09 on 2008-11-07
I'm not sure that envyng works in Intrepid. Be good to hear from someone who knows.

---

### Post by dabl on 2008-11-07
It works great on my Kubuntu 8.10 rig.  But it sounds like there can be problems with python, under Gnome.

---

### Post by mattkoehn on 2008-11-07
Well I found a link to a thread that helped me while searching for the answer to the error for the command you gave me. But i wouldn't have figured this out without the new command. Sadly the error in envy was because I have two video cards and it didn't know which one to use. Apparently this version of X needs us to manually define which card we plan on using with the bus id in xorg.conf. 

[http://ubuntuforums.org/showthread.php?t=607001](http://ubuntuforums.org/showthread.php?t=607001)

For anyone that finds this thread with the same issue, run lspci to find the bus id which needs to be added to the device section of xorg.conf. The format is:

BusID "PCI:2:a:1"

---

### Post by dabl on 2008-11-07
Probably you could pull one card, run EnvyNG to install the driver, then install the second card and add the two lines with the PCI bus ID of the cards to the xorg.conf file.  Just guessing -- one card is enough for me.  LOL

---

### Post by chrisinspace on 2008-12-02
> **Peter09 said:**
> I'm not sure that envyng works in Intrepid. Be good to hear from someone who knows.

This worked great for me.  I tried for 2 days to get an old GeForce2 card to work.  The card I normally use died, so I pulled this older one out of mothballs until I can get a replacement.  The Ubuntu wizard kept loading the 96 driver, but X would fail when I tried to boot.  EnvyNG worked like a charm.  I booted to the desktop in low graphics mode, ran envyng -t in the terminal and used it to install the 96 driver.  After a reboot, everything is working perfectly.

---

### Post by chrisinspace on 2008-12-02
Oh...and in response to Peter09, I am using Intrepid.  The machine in questions is running Mythbuntu 8.10 w/ XFCE.

---

