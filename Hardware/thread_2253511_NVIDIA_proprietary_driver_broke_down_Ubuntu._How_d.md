---
title: "NVIDIA proprietary driver broke down Ubuntu. How do I go back to open source driver?"
date: 2014-11-20
forum: Hardware
---

### Post by Novitk on 2014-11-20
I have an optimus notebook, which means I have 2 video cards: an integrated intel card and a dedicated GeForce GT 730M. I've installed Ubuntu 14.04 and everything was fine as long as I was using the open source driver (nouveau). But then I installed the proprietary driver by going to **Settings >> Softwares and Updates >> Additional Driver >> (selected) Using NVIDIA binary driver - version 331.38 from nvidia-331-updates**. After restarting, the whole graphical interface was frozen, I couldn't even get to the login screen. Although graphical features are broken, It seems the rest of the system is working because I can switch to another TTY (ctrl+shift+F1) and everything works fine on text mode only, so I guess I could somehow revert to the open source driver. The problem is that I selected the proprietary driver using a graphical procedure, so I don't know how I could revert it now that I don't have graphical support.

My question is: considering my graphic is broken, how can I revert what I did and set my Nvidia card driver to the open source (nouveau) again? Thanks in advance for your attention.

---

### Post by grahammechanical on 2014-11-20
You can try this.

At the Grub boot menu select Advanced Options For Ubuntu and when the sub-menu opens select Recovery Mode. At the recovery menu select Resume. That will load Ubuntu using an open source video driver called llvmpipe. It is not as effective as Nouveau but it is useful as a fall back video driver.

Then when you are at the desktop you can change video drivers using Additional Drivers again.

Regards.

---

### Post by Novitk on 2014-11-20
It didn't work. I tryed to resume, I tryed the failsafex too etc... nothing worked. I can't get past the login screen. I guess the generic video driver can't handle my dual video cards. But as I said, I can go to another TTY, so if there is a way of reverting things back in texto mode only, I think I could do the procedure in my system current state.

---

### Post by oldfred on 2014-11-20
Some more info:

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)

      
 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Unless you blacklisted or purged nouveau, it may revert to that. 
But I thought most systems then just used the internal Intel video chip & that may need its own boot parameters.
      
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Novitk on 2014-11-21
> **oldfred said:**
> Some more info:

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)

      
 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Unless you blacklisted or purged nouveau, it may revert to that. 
But I thought most systems then just used the internal Intel video chip & that may need its own boot parameters.
      
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Purging nvidia packages solved the issue and nouveau is back as default driver. Thanks!

---

### Post by Novitk on 2014-11-21
By the way, just a tip for those who have an Nvidia Optimus notebook too. The problem happaned with "nvidia-331-updates", which is the most bleeding edge driver and is not extensively tested. The good news is that the problem didn't happened (so far) with the package "nvidia-331", which has been tested by Ubuntu community. It's a viable alternative to the open source nouveau driver.

---

