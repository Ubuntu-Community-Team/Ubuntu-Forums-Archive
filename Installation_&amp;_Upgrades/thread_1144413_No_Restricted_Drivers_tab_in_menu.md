---
title: "No Restricted Drivers tab in menu"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by misterf1 on 2009-04-30
Hello everyone, I've been with Ubuntu since Feisty and I have had an up and down experience, mainly because of Xorg.  So my upgrade to Jaunty has raised a few problems.  I wanted to give Compiz another go since it crashed my system back in the Feisty days.  So I've been living in basic mode ever since.  I tried to edit my xorg.conf file because Ubuntu has always defaulted to 800x600 on startup.  But the Nvidia driver would sort it out by auto checking what the monitor could do (1440x900).  Only today was I brave enough to try and get Compiz (Desktop effects) and a booted 1440x900 setup.  I tried purging Nvidia and reloading 180xx, but I don't have a restricted drivers tab to even try to apply the driver.  Too weird.  Unfortunately I did not back-up my xorg from how it was, but at this point, I can't even get the driver to reload.  Thoughts?

---

### Post by doas777 on 2009-04-30
you might want to open and close Synaptic Package Manager to refresh your repository lists, or run ```
sudo apt-get update
```.
then go back to System -> Administration -> Hardware Drivers and check whether you now have drivers.

also run ```
sudo lshw -C Display
``` to make sure it is recognizing your card.

if it's not working, but detecting correctly, download envyng (in synaptic ) and use it to install the driver. BTW, it wasn't until jaunty that i could get the 180 driver to work on several of my machines. you may just have to use 177 or 173.

you also may want to reset your xorg to default, with 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```.
then use nvidia-settings to configure your vid to your desired res.

---

### Post by misterf1 on 2009-04-30
thanks man.  So I have an update.  For some reason, 180.51 has found its way back on to my machine and the Nvidia applet recognizes it.  However, I still get no desktop effects (button doesn't work in Control Centre) and there are a few anomalies (wastebasket stuck in the middle of the bottom bar).  Still no hardware manager for drivers, its just not in the list.  I get System>Administration...but there is no Restricted Hardware like there was in previous distros.  I'll give your suggestion a bash and see if I can get somewhere with it.

---

### Post by misterf1 on 2009-05-02
So I've been struggling with this for a few days now.  I've purged nvidia and tried loading 173, 180, glx and non-glx, but all with no luck.  The restricted drivers option in administration still does not show up in the menu and I have no way of applying the new drivers that I have downloaded.  The nice thing is that Unbuntu no longer loads in 800x600, which is nice.  I would just like to be able to try and use Ubuntu now like it's meant to be.  

I also pulled my other video card, so I am running non-sli now since I saw in another post that 9.04, 180, and sli do not mix.  thoughts?

---

### Post by doas777 on 2009-05-03
I'm not qualified to help with SLI, but have you followed the instructions above to update apt-get's list of softwares? also if you go to System -> Administration -> Software sources, do you have the all the repositories enabled?

---

