---
title: "Offline install of Nvidia 180 on 8.10"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Taemojitsu on 2009-02-12
I've been trying to get Ubuntu 8.10 working on an Asus laptop that doesn't have a network connection. Codecs and the nvidia driver are the biggest problems. When I install the nvidia-glx-180 package and all its dependencies including the kernel source package, it successfully installs and gives no errors. When I reboot my notebook, it stops after the Ubuntu loading screen, the screen goes black and the cursor goes into the busy icon.

I have been trying to research how to fix this, the first time it happened I was using drivers off the daily Jaunty live dvd and I thought it wasn't compatible somehow (I also installed by clicking on it in gnome, not by using a package manager to let me register other packages as dependencies) and I just reinstalled because of Ubuntu not loading afterwards. But now having used the Intrepid nvidia-glx-180 package (I think there's no difference) it has the same problem.

Pressing the power button makes my notebook go thru the shutdown steps in Ubuntu, even tho the desktop never loaded. From what I understand, it is either a problem with Compiz not loading or the driver isn't loading because of a bad xorg.conf. I tried looking at the xorg.conf on my installation using a Live USB to boot, but it's the practically-blank version used in current X (I don't know much about it) and I didn't know how to make it accept Nvidia, or if that was even the problem.

I'm pretty much ready to manually edit it now, or if that fails install using Nvidia's shell script, or if that fails try the default version that shows up in Hardware Drivers by loading the packages onto my (offline) notebook somehow... but can anyone explain, is this a problem with Intrepid that causes it not to work when the package is installed, and not having an xorg.conf that works with the driver? Is it because I installed it offline, using packages downloaded and transferred by flash drive? Is it a bug with the debian package for the 180 driver? Is it not the xorg.conf at all, but something to do with my video card or other hardware?

Thanks!

Oh, one more thing. If that does happen. How do I revert the driver without reinstalling Ubuntu, which I've already done too many times to count (learning how to dual-boot)? :&#8203;P From what I USED to understand, it would have been by changing 'nvidia' in xorg.conf back to 'nv', but my xorg.conf doesn't have either because of its new dynamic configuration which I don't understand at all!

Update: it wasn't the driver at all, it was a package from Jaunty that I installed to get codecs. Don't know which one, but somewhere along the way, one of the packages or dependencies for Jaunty VLC from medibuntu or the Jaunty gstreamer packages from ubuntu-restricted-extras ended up preventing X from starting on my 8.10 system. I guess this is why Ubuntu versions exist!

---

