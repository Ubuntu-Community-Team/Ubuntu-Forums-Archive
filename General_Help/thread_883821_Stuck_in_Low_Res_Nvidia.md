---
title: "Stuck in Low Res Nvidia"
date: 2008-08-08
forum: General Help
---

### Post by joeyknuccione on 2008-08-08
I used Envy to try to get the correct nvidia driver. Now I'm stuck in low res mode. Jockey doesn't give me a driver option. Nvidia settings says I'm not using nvidia x server. If I try to change resolution it says something about xrand r or something. Please help, this is a work laptop.

---

### Post by tuxxy on 2008-08-08
Did you recently and video settings? also did you try and install through jockey first? Did the drivers ever work?

You could try adn reconfigure the xorg to get out of low graphics mode and reinstall the drivers

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by PmDematagoda on 2008-08-08
What are the specifications of the laptop?

---

### Post by joeyknuccione on 2008-08-08
> **PmDematagoda said:**
> What are the specifications of the laptop?

I did the guy above you's idea, and I'm at least back to 800 res, but capable of 1400

Laptop:
HP dv9235nr
CPU: Intel Core2 T5200 @ 1.6G
       width: 64 bits
Ram Tech: DDR 2 SDRAM
Ram Form: SO DIMM 200-pin
Video: nVidia G70 [GeForce Go 7600]
	width 64 bits
	clock: 33 MHz
Video Memory: 256 MB
Display: 17 in TFT active matrix Wide Screen WXGA+
Audio: Intel 82801G (ICH7 Family) HiDef 
	width: 64 bits
	clock: 33 MHz
Wireless: PRO/wireless 3945ABG
	width: 32 bits
	clock: 33 MHz
Ethernet: Intel 82573L Gigabit ENet Controller
	   width: 32 bits
           clock: 33 MHz
OSes:Vista, XP, UbuntuHH/SE

---

### Post by tuxxy on 2008-08-08
If you are out of low graphics have you tried enabling the driver in jockey?

---

### Post by joeyknuccione on 2008-08-08
> **tuxxy said:**
> If you are out of low graphics have you tried enabling the driver in jockey?

Jockey does not offer any drivers. I know before I would use nVidia 'latest' driver in synaptic, but that driver doesn't seem available anymore. Right now I'm showing envy gave me the nvidia-glx-new-envy setup, but I'm not getting my 14xx resolution.

---

### Post by tuxxy on 2008-08-08
Have you tried installed and attempted changing the resolution in nvidia-settings?

---

### Post by joeyknuccione on 2008-08-08
> **tuxxy said:**
> Have you tried installed and attempted changing the resolution in nvidia-settings?

Now I'm stuck in 14xx resolution. If I try nvidia-setting I get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

When I follow those directions, I get the same error. Then if I try Sys>Pref>Resolution I get:

The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

---

### Post by strange_cathect on 2008-08-12
I can confirm this behavior. I started a thread on this subject too: 

> [http://ubuntuforums.org/showthread.php?t=886519](http://ubuntuforums.org/showthread.php?t=886519)

---

### Post by dark_helmut on 2008-10-06
[POSSIBLE SOLUTION??]

Athlon-X2 4200+
Geforce 7300 LE

Hi all,

I just installed ubuntu 8.04 64bit edition the other day and have had tremendous trouble with it regarding the installation of nvidia drivers. I tried basically everything that the forums said nothing worked. I ran into a variety of problems from incredibly slow performance with the envyNG drivers to the unrecognition of the drivers and forced low-res mode described above. It got to the point where I was too frustrated to continue so I installed ubuntu 7.10 I then installed the nvidia-glx-new drivers using the synaptic package manager and then enabled them by selecting the option in System->Administration->Restricted Package Manager and to my extreme delight it finally worked (but for how long??). 

Heres where I think I can help...

The nvidia-glx-new package was installed and everything was working great, however I wanted to adjust my brightness so I decided to install nvidia-settings using 'sudo apt-get install nvidia-settings' (Thankfully, before I did this I copied the /etc/X11/xorg.conf file). Everyhting appeared to work great at first, but then on Reboot Bam!! Forced Low-Res mode.
I looked at the xorg.conf file that was replaced after I installed nvidia-settings and it was all messy, the previous file which I backed up described the model of my video card and specified that it was all nvidia the new file did none of this. Therefore, I believe that nvidia-settings, and not the drivers may have also been the culprit for 8.04s behaviour. I took the following steps and now ubuntu is working again with the Drivers and Desktop Effects.

-removed nvidia-settings using 'sudo apt-get remove nvidia-settings'
-removed all xorg.conf.failsafe, xorg.conf~, etc. that was added by successive failed boots.
-copied my backup xorg.conf file (with working settings) and overwrote xorg.conf with it.
-disabled nvidia drivers in restricted package manager (this was kind of weird because i tried sudo apt-get remove nvidia-glx-new and it said it wasnt installed)
-rebooted comp (it asks you to)
-on restart ubuntu booted properly but I did not have the restricted drivers and could not access special effects.
-i then searched in synaptic package manager for nvidia and clicked to install the nvidia-glx-new drivers again
-enabled the drivers in restricted package manager
-reboot and worked again

Im not sure if this will work for you or for 8.04 but I figured it be worth it to post it because this was a very frustrating issue for me. And regardless if it works or not it may shed some light that perhaps nvidia-settings and not the drivers that is causing problems.

Hope this helps.

---

### Post by shadowfirebird on 2008-10-07
FWIW I have a 7300 and exactly the same problem, even down to the hardware screen ("jockey") not showing my graphics card.

I'm running the Xorg "vesa" driver at the moment, which is a sort of an emergency fallback.  It gets me 1280x1024 on my monitor, though.


Sorry I don't have a solution.  If you want my emergency fallback, you'll probably need to install just "xserver-xorg-video-nv" (I don't know why); get rid of all the packages with "nvidia" in, and if that doesn't do it change your x11.conf.  Let me know if you want more details.

You might also try that Xorg "nv" driver, which has worked for me in the past.  But, again, no 3d.

---

