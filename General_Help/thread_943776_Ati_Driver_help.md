---
title: "Ati Driver help"
date: 2008-10-10
forum: General Help
---

### Post by crapple on 2008-10-10
I have an ati radeon 7500.  All I got was a black screen on hardy and the same with interpid.  Then I downgraded the ati driver to this one [http://packages.debian.org/etch/xserver-xorg-video-ati]("http://packages.debian.org/etch/xserver-xorg-video-ati")
So it gave me errors in the terminal so I did ```
sudo dpkg -i --force all xserver-xorg-video-ati_6.6.3-2_powerpc.deb
``` Then ubuntu ran in low graphics but how to I get it to run in high graphics.  I think it is something with the new driver.  I am running this on g4 powerpc.  Is there a way to fix the driver?

Thanks

---

### Post by thegner on 2008-10-10
> **crapple said:**
> I have an ati radeon 7500.  All I got was a black screen on hardy and the same with interpid.  Then I downgraded the ati driver to this one [http://packages.debian.org/etch/xserver-xorg-video-ati]("http://packages.debian.org/etch/xserver-xorg-video-ati")
So it gave me errors in the terminal so I did ```
sudo dpkg -i --force all xserver-xorg-video-ati_6.6.3-2_powerpc.deb
``` Then ubuntu ran in low graphics but how to I get it to run in high graphics.  I think it is something with the new driver.  I am running this on g4 powerpc.  Is there a way to fix the driver?

Thanks
I'm not certain as to exactly which cards it supports, but "envy" is an excellent program for installing nvidia and ati drivers. It is a very well written program, which is, as of 8.04, available in the repositories.

sudo apt-get install envy

should install it and you can find it on the applications menu somewhere...

HTH,

Travis

---

### Post by crapple on 2008-10-10
Envy did not work I tried it.

---

### Post by jocko on 2008-10-10
> **crapple said:**
> I have an ati radeon 7500.  All I got was a black screen on hardy and the same with interpid.  Then I downgraded the ati driver to this one [http://packages.debian.org/etch/xserver-xorg-video-ati](http://packages.debian.org/etch/xserver-xorg-video-ati)
So it gave me errors in the terminal so I did ```
sudo dpkg -i --force all xserver-xorg-video-ati_6.6.3-2_powerpc.deb
``` Then ubuntu ran in low graphics but how to I get it to run in high graphics.  I think it is something with the new driver.  I am running this on g4 powerpc.  Is there a way to fix the driver?

Thanks

The driver you installed is old and not for ubuntu. There is very little chance that you will get it to work, as it is compiled in a different kernel version and for a different xorg version. The reason you get low graphics mode is because xorg can't find a proper driver (as you have replaced it with a non-functional one) and resorts to using the vesa driver.
The correct driver version is already installed by default in ubuntu, so you are probably better off if you reinstall that.

One probable cause to the problem with your screen going black (when you are using the correct driver) is if xorg is trying to use a resolution or refresh rate that your monitor can't display.
One thing to try (do this while you are still in the low graphics mode):
Find out the horizontal sync and vertical refresh rate ranges for your monitor (check the manual or the manufacturer's webpage). Add them to the monitor section of your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```Make it look something like this (only add the blue lines, but with the correct numbers for your monitor. Don't change anything else for now.):
```
Section "Monitor"
    Identifier     "Monitor"
    [COLOR=Blue]HorizSync       30.0 - 75.0
    VertRefresh     60.0[/COLOR]
EndSection
```Then uninstall the debian driver and reinstall the ubuntu driver (use synaptic), reboot and keep your fingers crossed.

And: Envy only works for downloading restricted drivers. As ATI doesn't support such old cards, there is no restricted driver available for a radeon 7500.

---

### Post by crapple on 2008-10-11
This did not work.  The only way I can get any sort of graphical interface is installing an old driver like I had to do in Gusty but hardy and intrepid don't let you do this.  Is the another driver or a way to reconfigure or recompile this driver?  

Thank you

---

### Post by jocko on 2008-10-11
> **crapple said:**
> Is the another driver or a way to reconfigure or recompile this driver? 

I don't think so. Even if it may be possible to patch and recompile the old driver to get it working on a newer xorg version, it's probably going to be a lot easier to get the preinstalled driver working.

---

### Post by crapple on 2008-10-11
How do I get the preinstalled driver working?

---

