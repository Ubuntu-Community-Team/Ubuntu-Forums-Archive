---
title: "Screens found, but none have a usable configuration"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by rstoya05-lx on 2009-09-06
I am unable to install the Ubuntu sanctioned NVidia binary driver. When I restart Ubuntu shows a screen titled "Ubuntu is running in low-graphics mode" with the following detail:

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) NVIDIA(0): Please see the COMMON PROBLEMS section in the README for 
(EE) NVIDIA(0): additional information
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0): Screen(s) found, but none have a usable configuration

I understand this a binary driver that is not supported but perhaps you can give me some clues as to how to interpret what's going on or how to debug.

---

### Post by hal10000 on 2009-09-06
Where did you get the driver from?
I recomment installing not the one from the nvidia download-page, but from the ubuntu repositories.
You should just call your hardware driver-manager (under kde it's called jockey-kde and i guess in gnome it's jockey-gtk) and follow the instructions.

---

### Post by rstoya05-lx on 2009-09-06
Yes I've installed one that is sanctioned by Ubuntu. I did not see by the way anything under System -> Administration -> Hardware Drivers (same as jockey-gtk I believe) so I did the following instead:

1) Applications -> Add/Remove... -> System Tools.
2) Install "NVIDIA X Server Settings" and "NVidia binary X.Org driver ('version 173' driver)". 
3) Run 'sudo nvidia-xconfig' to modify xorg.conf to use the binary driver.
4) sudo reboot

At first I saw the message "no device found". Eventually I figured that's because this laptop has 2 graphics cards (one is on-board I think and the other is GeoForce 9300M GS). I ran 'lspci | grep VGA' to figure out the bus id GeoForce uses and then added the this to the device section of xorg.conf:

BusId "PCI:1:0:0"

I have purposely stayed away from downloading from the nvidia web site. I know that doing so requires more work when upgrading to the next version of Ubuntu, etc.

Any other suggestions?

---

### Post by hal10000 on 2009-09-06
Are you running an older ubuntu-version, like intrepid (8.10) or so, which doesn't have jockey, i think? If so, you have to install the pckages manually:
In the ubuntu-repos there are some packages related to nvidias graphic drivers: [COLOR="Red"]linux-restricted-modules[/COLOR], [COLOR="Red"]nvidia-common[/COLOR], [COLOR="Red"]nvidia-glx-173[/COLOR], [COLOR="Red"]nvidia-kernel-common[/COLOR] and (optional) [COLOR="Red"]nvidia-settings[/COLOR]. Make sure they are all installed.

---

### Post by rstoya05-lx on 2009-09-06
> **hal10000 said:**
> Are you running an older ubuntu-version, like intrepid (8.10) or so, which doesn't have jockey, i think? 


Ubuntu 9.04

> **hal10000 said:**
> 
If so, you have to install the pckages manually:
In the ubuntu-repos there are some packages related to nvidias graphic drivers: [COLOR="Red"]linux-restricted-modules[/COLOR], [COLOR="Red"]nvidia-common[/COLOR], [COLOR="Red"]nvidia-glx-173[/COLOR], [COLOR="Red"]nvidia-kernel-common[/COLOR] and (optional) [COLOR="Red"]nvidia-settings[/COLOR]. Make sure they are all installed.

I was missing a couple of the packages so I added them manually. Then I was able to run jockey-gtk and activate version 180 of the binary driver. After rebooting I got the same message from the original post above.

Thanks for your help. What next?

---

