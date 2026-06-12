---
title: "Ubuntu 8.10 configures all hardware, Kubuntu doesn't?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by TaoMind on 2008-12-04
Group, 
    Please bear with me on this long post... I'm a little new to Linux, but was under the assumption that the basic differences between the 'buntu' distro's were the actual window managers and the accompanying packages. But now wonder if there isn't a larger difference in the kernal or core applications. Last week I bought the necessary parts to build a new PC strictly for Linux (new to Linux, but not computers...). I bought an Asus P5Q motherboard and an MSI 9800GT nVidia based graphics card. I had Unbuntu Hardy 8.04 installed on my old PC and have a DeLL Studio 1534 with Ubuntu on it as well, my goal was to run Kubuntu on my new system due to some of the multimedia apps (i.e. Amarok, etc.). I installed a fresh Kubuntu 8.10 64bit desktop and had problems right off with it recognizing my Ethernet card (Atheros based). Luckily I was able to find a solution from my laptop which involved copying some drivers via thumb drive and compiling some downloaded drivers on the desktop... Success! Network up and running. Then time to tackle the 2nd problem, no 3d acceleration for the nVidia based 9800GT, I select the recommended 'proprietary' drivers and reboot to enable the 3d desktop affects, so far so good. Problem comes after the reboot, now I no longer have sound..., I research the issues, see a few posts about nVidia drivers breaking the sound and try the recommended solutions, no joy. In the meantime, I update with all the latest packages and notice when I receive a kernel update my Ethernet stops working again, so I recompile the drivers with the new kernel and I'm back up running again on the network. Ok, not satisfied with no sound, I then format and start over only to duplicate the same issues as above, no auto-discovery of my embedded network card, no 3d graphics and sound at the same time, etc. I finally break down, format again and install Ubuntu 8.10 64bit and have had no problems with any of my hardware... Network card found and configured automatically, accelerated graphics drivers installed without problems when prompted and I still have sound! Just curious how there could be such a difference in core functionality between the two though they are same version releases?
   Also, what is the chance that installing the Kubuntu KDE desktop now on top of the Ubuntu desktop might cause issues as noted above with either Kubuntu or (worse) my working Ubuntu desktop?
   Would appreciate any thoughts on this...

---

### Post by ColJep on 2008-12-07
I have a similar problem. I have been using Ubuntu on my main machine since about 6.10. It is now on 8.04.

I have been looking at Kubuntu but never thought any were ready for "prime time". I have a spare machine which I set up to try Ubuntu 8.10 and was well impressed. Everything worked including my old bugbear Sticky Keys. Which I had raised on Launchpad.

Motherboard is a KT600 with Nvidia GeForce 7600GT 256MB video card, Athlon XP 2800 and 512MB ram. The video card worked with the recommended 177 version driver.

I decided to install a separate Kubuntu installation on a new partition. The video card was recognized so i activated the 177 driver. All seemed ok until I tried to look at the Display applet. Black screen and monitor (Benq 17 inch LCD 781) complaining of being "out of range".

A series of attempts to get a fully working video ended with a new install and finding a hidden version 96 which does seem to work.

I now intend to set up Ubuntu and Kubuntu on separate partitions with a shared partition for the /home folder. This I hope will show the true difference between the versions.

I understand there are issues with the Nvidia drivers which are waiting on Nvidia.

---

