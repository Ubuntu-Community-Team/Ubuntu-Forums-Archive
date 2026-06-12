---
title: "Thinkpad t400 ATI 3470 HD video driver"
date: 2008-09-22
forum: Hardware
---

### Post by robertpolson on 2008-09-22
If anyone managed to install ATI drivers for thinkpad t400, please post how specifically did you do so ?

---

### Post by mglukhovsky on 2008-09-22
Using 8.04 (Hardy Heron) I disabled the switchable graphics option in the BIOS (pressing F1 or the ThinkVantage key during boot gets you to the BIOS) by going to the Display options, setting it to Discrete only and disabling OS autodetection. Then the Restricted Drivers manager installs and sets up the ATI fglrx drivers normally.

The issue, as far as I can tell (and please correct me if I'm wrong) is that the Intel card appears as the first device that Xorg sees when switchable graphics are enabled. The ATI card is second. That means that when Xorg launches, it doesn't know what to do. Removing the Intel card from the precedence clears up the confusion.

Maybe someday in the distant future we'll be able to take advantage of switchable graphics. Until then, we're stuck with poor-quality fglrx drivers.

---

### Post by robertpolson on 2008-09-22
How exactly did you install ATI drivers ?

Do you also experience flickering when watching videos when compiz is enabled in a a small (not full screen) mode ?

---

### Post by mglukhovsky on 2008-09-23
Honestly, I just used the Restricted Drivers manager and it detected everything fine on reboot (once Switchable Graphics were shut off).

And yes, I do experience flickering when using certain output modules with Compiz. It's a bug with the ATI drivers. You can try either using the Xv output module in VLC (worked well enough for me) or switching to Metacity instead of Compiz. For now, it seems you have to choose between slick animations and smooth full-quality video.

---

### Post by robertpolson on 2008-09-23
This takes care of the flickering:

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by MaX PL on 2008-09-29
Would this be the driver: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html) if I wanted to use 8.04 64 bit?

---

### Post by boubalos on 2010-03-05
# I successfully install ati driver on my T400 ubuntu 9.10(karmic), with full 3D accelerate and no GUI(maximize and minimize window) delay. Following is how I did:

# Use ATI propriety driver ati-driver-installer-9-12-x86.x86_64.run. I think ati-driver-installer-9-10-x86.x86_64.run is also ok. However, ati-driver-installer-9-8-x86.x86_64.run does not support 9.10 and could cause problem(black screen, and can not go into GUI). 


> sudo sh ./ati-driver-installer-9-11-x86.x86_64.run 

# After finishing installation in GUI, then
> sudo dpkg-reconfigure xserver-xorg
> reboot

# At this time, the ati driver is successfully installed with 3D acceleration. However, the UI suffers serious time delay when opening, minimizing, or maximizing a window. Sometimes, even a user application's GUI(graphic user interface) also suffers. So following command could solve the problem. At that time, ATI driver would run perfectly .

# Adding a PPA to your Ubuntu system(for knowledge of PPA, see [https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview](https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview))
> sudo add-apt-repository ppa:launchpad-weyland/ppa

# Add /etc/apt/sources.list these sources:
deb [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main

# then 
>  sudo apt-get update
>  sudo apt-get upgrade 


# then enjoy!


# For more reference:

[http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html](http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html)
[http://linux.chinaunix.net/bbs/archiver/tid-1153115.html](http://linux.chinaunix.net/bbs/archiver/tid-1153115.html)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)
[http://www.xiaoheiclub.com/thread-352-1-1.html](http://www.xiaoheiclub.com/thread-352-1-1.html)
[http://www.lijikun.net/2008/12/t400.html](http://www.lijikun.net/2008/12/t400.html)

---

### Post by boubalos on 2010-03-05
# I successfully install ati driver on my T400 ubuntu 9.10(karmic), with full 3D accelerate and no GUI(maximize and minimize window) delay. Following is how I did:

# Use ATI propriety driver ati-driver-installer-9-12-x86.x86_64.run. I think ati-driver-installer-9-10-x86.x86_64.run is also ok. However, ati-driver-installer-9-8-x86.x86_64.run does not support 9.10 and could cause problem(black screen, and can not go into GUI). 


> sudo sh ./ati-driver-installer-9-11-x86.x86_64.run 

# After finishing installation in GUI, then
> sudo dpkg-reconfigure xserver-xorg
> reboot

# At this time, the ati driver is successfully installed with 3D acceleration. However, the UI suffers serious time delay when opening, minimizing, or maximizing a window. Sometimes, even a user application's GUI(graphic user interface) also suffers. So following command could solve the problem. At that time, ATI driver would run perfectly .

# Adding a PPA to your Ubuntu system(for knowledge of PPA, see [https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview](https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview))
> sudo add-apt-repository ppa:launchpad-weyland/ppa

# Add /etc/apt/sources.list these sources:
deb [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main

# then 
>  sudo apt-get update
>  sudo apt-get upgrade 


# then enjoy!


# For more reference:

[http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html](http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html)
[http://linux.chinaunix.net/bbs/archiver/tid-1153115.html](http://linux.chinaunix.net/bbs/archiver/tid-1153115.html)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)
[http://www.xiaoheiclub.com/thread-352-1-1.html](http://www.xiaoheiclub.com/thread-352-1-1.html)
[http://www.lijikun.net/2008/12/t400.html](http://www.lijikun.net/2008/12/t400.html)

---

### Post by jfabrizio on 2010-04-03
I've followed your instructions.
But, I have dowloaded from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English") last driver (version 10.3) and I have used it!

So, I have problem with 
> # Add /etc/apt/sources.list these sources:
deb [http://ppa.launchpad.net/launchpad-w...ackfill/ubuntu]("http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu") karmic main
deb-src [http://ppa.launchpad.net/launchpad-w...ackfill/ubuntu]("http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu") karmic main

when I run the command 
> sudo apt-get update
the output is:
```
W: Failed to fetch http://ppa.launchpad.net/launchpad-weyland/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Why?

Thank you in advance.
Fabrizio

---

### Post by boubalos on 2010-04-04
I think you may have included "http://ppa.launchpad.net/launchpad-weyland/ppa/ubuntu karmic main" in your sources.list  or Synaptic Package Manager.  Delete this source, and try again?

Anyway, I think this problem do not affect fixing the ati problem.

---

### Post by vancouverite on 2010-05-12
Hi all,
I have successfully installed the ATI drivers on my t400, but am sick and tired of the memory leak (see below). 

Has anybody successfully retrograded to the Intel driver?  If I remove the ati driver section in xorg.conf, restart and switch my graphics card, will it just work, or do I need to install the intel dirvers first?

Thanks.

+++++++++++++++++ Memory leak
If you don't know what I mean by the memory leak, have a look at your memory usage after 2-3 hours of up time, if your computer is like mine it, will be 1.1+ GB.  Keeping the memory usage in sight, open the Catalyst Control Center, go to powerplay, change its state (either from on to off, or from off to on) and hit Okay (not apply).  Watch your memory usage suddenly drop to 600 MB.  This leak never goes above 1500 GB, but still - that's huge!

---

### Post by regiss on 2010-07-08
> **vancouverite said:**
> Hi all,
I have successfully installed the ATI drivers on my t400, but am sick and tired of the memory leak (see below). 

Has anybody successfully retrograded to the Intel driver?  If I remove the ati driver section in xorg.conf, restart and switch my graphics card, will it just work, or do I need to install the intel dirvers first?

Thanks.

+++++++++++++++++ Memory leak
If you don't know what I mean by the memory leak, have a look at your memory usage after 2-3 hours of up time, if your computer is like mine it, will be 1.1+ GB.  Keeping the memory usage in sight, open the Catalyst Control Center, go to powerplay, change its state (either from on to off, or from off to on) and hit Okay (not apply).  Watch your memory usage suddenly drop to 600 MB.  This leak never goes above 1500 GB, but still - that's huge!


Hi mate, 

did you find a way to install ati drivers for T400 and avoid memory leak. I can run ati drivers approximately 1 day then system freeze. And only way is hard restart. 

Cheers Ondra

---

### Post by boubalos on 2010-09-16
T400 use ATI card&#12290;After installing ubuntu 10.04 and using the official driver, many problem occur, such as&#65292;maximize time delay&#65292;machine become dead sometimes&#65292;and screen lightness can not be set in power management &#65292;and some CAD(such as pointwise, tecplot,etc) can not be perfectly used under “normal" or "extra" visual effects. 

I use this ppa&#65292;then every thing is solved, except thunderbird gains a little problem. I install the newer version thunder3.1, then a nearly perfect machine I gain.

ppa:
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid)


&#65374;&#65374;
I do not know if this have something to do with my resetting gnome&#12290;To reset gnome, rm these files under command line environment:
${HOME}/.gnome*
${HOME}/.gconf*
${HOME}/.metacity
${HOME}/.nautilus
/tmp/gconfd-${USER}
/tmp/orbit-${USER}

---

