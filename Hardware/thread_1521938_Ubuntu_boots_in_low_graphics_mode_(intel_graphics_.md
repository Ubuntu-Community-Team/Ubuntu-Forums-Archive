---
title: "Ubuntu boots in low graphics mode (intel graphics card)"
date: 2010-07-01
forum: Hardware
---

### Post by bach on 2010-07-01
Dear Ubuntu gurus, 


I am running Ubuntu Linux 10.04 64 bits on a DELL Latitude E6510 notebook which has an integrated Intel GMA graphics card. I can oly boot to X by using the kernel option "i915.modeset=0". The problem is that the machine boots in low-graphics mode. I get the message:

"Ubuntu is running in low-graphics mode

Your screen, graphics card and input devide settings could not be detected correctly. You will need to configure these yourself."

I have a number of candidate solutions, but none worked. 

In the logs, I see

(EE) intel(0): No kernel modesetting driver detected

cribari@darwin:/var/log$ less Xorg.0.log | grep intel
(==) Matched intel as autoconfigured driver 0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
(EE) intel(0): No kernel modesetting driver detected.
(II) UnloadModule: "intel"

My kernel is

cribari@darwin:~$ uname -a
Linux darwin 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

(I have also tried a 2.6.34 kernel, but to no success.) 

My intel driver

cribari@darwin:~$ dpkg -l | grep xserver-xorg | grep intel
ii  xserver-xorg-video-intel                  2:2.12.0+git20100630~glasen~ppa1                X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-intel-dbg              2:2.12.0+git20100630~glasen~ppa1                X.Org X server -- Intel i8xx, i9xx display driver (debug symbols

More info:

cribari@darwin:~$ dmesg | grep -i mmc
[    0.784722] PCI: Using MMCONFIG at f8000000 - fbffffff
[    1.987252] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.386592] mmc0: Unknown controller version (2). You may experience problems.
[    2.386830] Registered led device: mmc0::
[    2.386941] mmc0: SDHCI controller on PCI [0000:03:00.1] using ADMA

Hints and suggestions are welcome. Thanks. 

Francisco

---

