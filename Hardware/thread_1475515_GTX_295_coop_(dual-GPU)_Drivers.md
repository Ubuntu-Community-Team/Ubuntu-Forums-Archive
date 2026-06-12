---
title: "GTX 295 coop (dual-GPU) Drivers"
date: 2010-05-06
forum: Hardware
---

### Post by renomcdonald on 2010-05-06
Alright, I just spent the last 5 hours trying to get nvidia drivers for my graphics card to work. I have had to reinstall Kubuntu 3 times (thankfully very fast :P) due to various non-working solutions. Yes I did manage to corrupt the boot sequence once#-o, I forgot why I did the other 2 times though. 

I've searched forums and Google all over but can't find a way to get drivers that would allow me to have my triple monitors. Oh did I mention my third GPU is a 9800GTX? I havn't even begun to search for the 9800 drivers (if needed) as the GTX295 is just as important. I can't progress with this install of Kubuntu 10.04 until I find these drivers. It's just that big of a chunk out of my workspace only having one monitor (not mirrored lol)

**recap:**
1) Triple monitors needed
2) desire hardware-acceleration. Physx is a bonus!
3) Kubuntu 10.04 x64
4) Also have 9800GTX as physx and third monitor export
5)dual-booting Win7 and Kubuntu
6) had to revert to default drivers as some nvidia drivers broke TTY switching from X server. (read a lot about this, no solution worked. Anyways next cold-boot said it crashed)

Help! ](*,)

---

### Post by renomcdonald on 2010-05-07
bump

---

### Post by dino99 on 2010-05-07
add this repo to your sources into synaptic:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

read on that page how to add it , then update and upgrade

[http://ubuntuforums.org/showthread.php?t=1475839](http://ubuntuforums.org/showthread.php?t=1475839)

---

### Post by darkenvy6 on 2010-05-07
I'm adding **ppa:ubuntu-x-swat/x-updates** as the repo right?

okay once it's added, how to I install the packages from THAT repo? I still have to search.... (no the update yields nothing.)

---

### Post by darkenvy6 on 2010-05-07
I manually installed all that I could by using sudo apt-get intall. 
                **ppa-purge** and **xserver-xorg-input-fpit**               installed fine but **xserver-xorg-video-intel** claimed it was already the latest. **nvidia-graphics-drivers** and **xorg-server** could not be found! 

And oh upod reboot got the following message:
**Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE)NVIDIA(0): The NVIDIA GPU at PCI:4:0:0 is not supported by the 173.14.22
(EE)NVIDIA(0):    NVIDIA driver.
(EE)NVIDIA(0) Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

---

### Post by darkenvy6 on 2010-05-07
It now works? I installed the drivers using the "HArdware Drivers" tool under system. This is what originally ruined my install of Kubuntu twice. Although this time I installed a few different things. In the repository I installed the following:
[B]

Modaliases for the NVIDIA binary X.Org driver[/B][I]
nvidia-current-modaliases
[/I]
**Transitional package for nvidia-185-libvdpau-dev**
nvidia-185-libvdpau-dev

**Tool of configuring the NVIDIA graphics driver**
nvidia-settings

Then installed the **NVIDIA accelerated graphics driver (version Current)** from "Hardware Devices"


Please note that I did uninstall that added repo from earlier in the thread do to the 200 series not being compatible. I believe that driver release is for the generation directly before it lol. Anyways next time I booted I was in a display above 800x600 :grin:

I am going to work with this now and see if this is the complete solution before I call the thread solved 8)

---

