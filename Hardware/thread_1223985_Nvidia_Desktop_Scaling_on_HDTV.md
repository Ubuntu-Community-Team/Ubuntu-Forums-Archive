---
title: "Nvidia Desktop Scaling on HDTV"
date: 2009-07-26
forum: Hardware
---

### Post by Mr. Spoon on 2009-07-26
Motherboard: ASUS M3N78-VM
GPU: Geforce 8200M IGP
nVidia driver version: 180.44
OS: Ubuntu Jaunty x64
TV: 50 inch Panasonic plasma running at 1280x720

I installed the nVidia drivers for my graphics card via "Hardware Drivers" on my HTPC. After rebooting, I noticed that my desktop was scaled improperly. It's only off by about 10-20 pixels on each side. I've messed with every scaling option in the Nvidia Control Panel, but none of the settings will scale my desktop properly. Is there an alternate way to set desktop scaling with nvidia cards?

---

### Post by 905jay on 2010-06-14
I recently purchased a Desll Latitude E6410 and it has the nVidia Quadro NVS chipset. In Windows 7, it has a portion under "Video and Television" for HDTV Scaling. It works like a charm. I hope they implement it for the Linux version soon.

---

### Post by ozzman2 on 2010-10-28
I've got the identical board.  It's in a dedicated HTPC hooked up to a Samsung 46" DLP.

1024x768 fits the TV perfectly, but looks crappy.  1280x720 looks great.  I set the overscan compensation in "NVIDIA X Server Settings" to about 100.  It looses a little bit of the bottom toolbar, but it's not a dealbreaker.

Currently using the proprietary driver (download from the Nvidia site).  Driver version is 256.53 with Ubuntu 10.04.

I recommend:
1. Blacklisting Nouveau
2. Installing latest proprietary driver from Nvidia website
3. Change a few settings in Compiz
(got the instructions from here: [http://tombuntu.com/index.php/2009/0...thout-tearing/]("http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/") )

-note-
After you blacklist Nouveau, you will have to manually re-install the  proprietary Nvidia driver whenever a new kernel update comes out.  ie.  don't delete the installation package, and write down the command to  re-initialize it from a prompt.

I know it sounds like a pain, but it's totally worth it.  It handles HD video flawlessly (sound stays in sync and everything).

One other thing:
The overscan compensation won't kick in until the NVIDIA X-Server Settings is initialized.  I added it to my startup programs.  (The command is "nvidia-settings").

Good luck.

---

