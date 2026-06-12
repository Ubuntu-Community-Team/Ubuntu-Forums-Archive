---
title: "Installing Nvidia drivers from site??"
date: 2009-08-10
forum: Hardware
---

### Post by fallenshadow on 2009-08-10
Recently my Nvidia 7650GS card broke so now I got a Nvidia 9600GT as a replacement. Only problem is that im running 8.04 and I have been struggling to try and install the drivers from the site.

This is what im trying to install: [http://www.nvidia.com/object/linux_display_ia32_185.18.31.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31.html)

I have already removed the enabled driver... anyone have any tips for installing the ones off the site? as the instructions do not work. :(

---

### Post by aysiu on 2009-08-10
**Step 1**
Forget about that website

**Step 2**
Make sure you have extra software repositories enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 3**
Install *envyng-gtk* using Synaptic. If you don't know how to use Synaptic, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step 4**
Run Envy NG from Applications > System Tools

---

### Post by fallenshadow on 2009-08-11
I was able to install the new driver but unfortunately it did not work so I quickly uninstalled it. However now after the ubuntu loading screen the monitor just flickers and I cannot log in. :(

Can any commands help me?

Or I can delete files that are causing the problem using this live CD im using. First I need help in diagnosing the problem.

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> I was able to install the new driver but unfortunately it did not work so I quickly uninstalled it. However now after the ubuntu loading screen the monitor just flickers and I cannot log in. :(

Can any commands help me?

Or I can delete files that are causing the problem using this live CD im using. First I need help in diagnosing the problem.


envy can be ran from command line 

sudo apt-get install envyng-core

sudo envyng -t

---

### Post by fallenshadow on 2009-08-11
I tried that already but it failed to install the package. Is there anybody that knows what should be in the important bootup folders so I can analyse what to delete to get things working... I think that the Nvidia driver might not be completely removed.

---

### Post by fallenshadow on 2009-08-11
Also should something called nvidia-kernel be present in /etc/init.d? I am thinking that maybe that should be removed if its causing problems.

---

### Post by Vakman on 2009-08-11
If you wish to install from that site and not use EnvyNG then follow this [HowTo]("http://ubuntuforums.org/showthread.php?t=1125400").

---

### Post by fallenshadow on 2009-08-11
Getting drivers is no longer my main concern as I just want to get my system display back. 

I have tried(plus countless other things):

```

nvidia-uninstall
dpkg-reconfigure -phigh xserver-xorg
apt-get install xserver-xorg-video-all

```
(All done in the root terminal, so no need for sudo in front)

and also xfix in the kernel recovery menu.

Display problems are making me go mental lately... it just gets upset so easily. :(

The real problem is I think there may be some nvidia configs that are upsetting proceeding to the normal display. (nvidia-settings.rc is 
already deleted)

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> Getting drivers is no longer my main concern as I just want to get my system display back. 

I have tried(plus countless other things):

```

nvidia-uninstall
dpkg-reconfigure -phigh xserver-xorg
apt-get install xserver-xorg-video-all

```(All done in the root terminal, so no need for sudo in front)

and also xfix in the kernel recovery menu.

Display problems are making me go mental lately... it just gets upset so easily. :(

The real problem is I think there may be some nvidia configs that are upsetting proceeding to the normal display. (nvidia-settings.rc is 
already deleted)



did you try envyng -- this will remove any old stuff and install latest driver....

---

### Post by fallenshadow on 2009-08-11
I tried to install envyng via command line but it did not install.

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> I tried to install envyng via command line but it did not install.


what does 

 sudo apt-get install envyng-core 


say?

---

### Post by fallenshadow on 2009-08-11
This command saved me:

```
su - username
```

I was able to switch user and use the up arrow to use the commands I used to install the official driver again. I now have a working display again but its at 800x600 and should be 1024x768.

However the graphics drivers don't work for whatever reason but they do configure x properly. Does Nvidia have a tool to select my own resolution? (Nvidia settings does not detect an installed driver)

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> This command saved me:

```
su - username
```I was able to switch user and use the up arrow to use the commands I used to install the official driver again. I now have a working display again but its at 800x600 and should be 1024x768.

However the graphics drivers don't work for whatever reason but they do configure x properly. Does Nvidia have a tool to select my own resolution? (Nvidia settings does not detect an installed driver)




[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by fallenshadow on 2009-08-11
One question... will this automatically remove the official driver I have installed?

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> One question... will this automatically remove the official driver I have installed?

well I would select yes on that option (gives you choices) and the let it reinstall it

---

### Post by fallenshadow on 2009-08-11
I tried but I got this message...

```
EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver. this might happen because your card is not supported by the driver or Envy's hardware detection failed.

```

So looks like I need an expert to help me get this installed graphics driver to actually work.

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> I tried but I got this message...

```
EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver. this might happen because your card is not supported by the driver or Envy's hardware detection failed.

```So looks like I need an expert to help me get this installed graphics driver to actually work.


am guessing you ran it with sudo...?

---

### Post by fallenshadow on 2009-08-11
No I ran it using the gtk GUI since I now have a GUI to work with.

---

### Post by SlugSlug on 2009-08-11
> **fallenshadow said:**
> No I ran it using the gtk GUI since I now have a GUI to work with.


when I used to use it I would alway goto TTY1 (ctrl alt F1) login and do 
sudo envyng -t

---

### Post by fallenshadow on 2009-08-12
Its okay now, I upgraded to 8.10, uninstalled the official Nvidia site one and installed the Ubuntu one! Its all working now after a bit of hassle but its soo worth it. 

Anywayz thanks for trying to help me! :KS :guitar:

---

