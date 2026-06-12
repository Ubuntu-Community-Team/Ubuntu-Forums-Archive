---
title: "ATI driver issues - guru needed"
date: 2008-10-11
forum: General Help
---

### Post by geometrikal on 2008-10-11
Hi all


My computer is a Dell Inspiron 6400 with 2 gig ram and a Mobility Radion X1400


I loaded Ubuntu 8.04 (2.6.24-16) up a few weeks ago and really like it. Everything working fine with all the extras added in (compiz, restricted, etc)

Then I downloaded Scorched3D and when playing the game the 3D graphics flicker.

Thinking this was a driver issue I downloaded the latest driver from ATI and installed as deb package as per instructions. This didn't fix the issue.

After this, the screensaver config screen would freeze up and cause some problems. Also skype video had a flicker.

So I uninstalled the packages in synaptic and rebooted the computer. This is where my trouble starts. The computer loads up and cannot find the graphics card or something, and starts in low graphics mode. Using synaptic I make sure that the linux-restricted-modules, xorg-driver-fglrx and xserver-xorg-video-ati drivers are installed. Still, when I reboot it starts in low graphics mode.


Any ideas how to fix this? I have a lot of software installed and I don't really wanna do a clean reinstall of the whole operating system. :)


Ross

---

### Post by geometrikal on 2008-10-11
Extra:

If I do:

```
sudo dpkg-reconfigure xserver-org -phigh
```

it will disable the proprietry drivers and clean the xorg.conf file and when I reboot everything looks nice. However as soon as I enable the proprietry drivers in System -> Administration -> Hardware Drivers the problem comes back

---

