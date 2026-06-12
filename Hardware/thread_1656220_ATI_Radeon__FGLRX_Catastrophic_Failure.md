---
title: "ATI Radeon / FGLRX Catastrophic Failure"
date: 2010-12-30
forum: Hardware
---

### Post by hateborne on 2010-12-30
Ok, after nearly 20h in the last 4 days...my patience is spent. :-\

I installed the proprietary drivers for the ATI Radeon 4300M device, and it all went to hell.

First display would not work at all out of BIOS. Used the live boot to restore default xorg.conf settings. 

Then FGLRX is producing system halting errors. Got it uninstalled with the ATI mess. Could boot strictly to console. After another few hours, got GUI actually loading again. However, aticonfig, fglrxinfo, and any related commands give "command not found".

I am relatively new to Linux, so I am unaware of what logs/lists I need to provide. I greatly appreciate any help.

-Hate

---

### Post by coffeecat on 2010-12-30
With the ATI Radeon 4*** series of GPUs, I very much doubt you need the proprietary fglrx driver. I'll go further - you probably don't want to use it at all. I use the mobility 4200 on my laptop and the Radeon 4350 on my desktop and I get perfectly adequate performance (for compiz and video playback) with the default open source driver.

You get a GUI - are you having any problems with it? Can you enable desktop effects? Did you install the proprietary driver for game playing? Do you need any help purging the remnants of the fglrx driver from your system?

---

### Post by hateborne on 2010-12-30
Sometimes the desktop gets STUPID lag when moving frames (guessing >3 fps).
No I cannot enable desktop effects.
Yes, I cannot run ANY 3d applications and the system is showing Plug'n'Play.

I tried apt-get purge followed by manually locating and removing directories. However, after doing so, it became pure console boot.

Any suggestion on how one might go about locating said open source drivers?

---

### Post by coffeecat on 2010-12-30
> **hateborne said:**
> I tried apt-get purge followed by manually locating and removing directories. However, after doing so, it became pure console boot.

Without knowing what you purged and what directories you removed, it is difficult to know what is going on. Removing system directories can be very damaging. You may have irretrievably broken your system.

> **hateborne said:**
> Any suggestion on how one might go about locating said open source drivers?

Normally, you don't need to. They are installed by default and will be enabled by default if you disable the proprietary driver.

I cannot guarantee the following will work, because you may have removed something essential in your attempt to purge the fglrx driver. Nevertheless, I suggest you try the following to get back to the open source driver to see what and what will not work. Boot up Ubuntu. Open a terminal. Run this command to uninstall any bits of the fglrx driver that are still present:

```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev 
```You now need to disable the xorg.conf file that is needed for the fglrx driver but is not needed for the open source ATI driver:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```If you get an error, double-check your typing. Pay attention to case - X11 = capital-x, eleven.

Now make sure you are connected to the internet and:

```
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core
```That will reinstall anything needed that may have been inadvertently removed.

Now reboot and see what happens.

---

### Post by hateborne on 2010-12-30
```
sudo apt-get purge fglrx*
```

A second one I cannot remember. Something dealing with "radeon".

I can enable full desktop madness, so that's a start. I've got to dig up some 3D app to test it. It is acting considerably more friendly so far.

Thank you

---

