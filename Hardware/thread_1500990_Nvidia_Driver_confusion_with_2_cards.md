---
title: "Nvidia Driver confusion with 2 cards"
date: 2010-06-03
forum: Hardware
---

### Post by danmarsden on 2010-06-03
I'm running Ubuntu 10.04 and have 2 graphics cards trying to run in a quad monitor setup which doesn't seem to be working.
Geforce 8500 GT PCIe-16
GeForce FX 5500 Stansard PCI (not PCIe)

If I run the old Nvida drivers 173.x both graphics cards are recognised and I can view/configure them in the Nvidia X Server settings ui.
The machine boots fine if I only enable the screens on the 8500 card, but if I try to enable the screens on the other card the screen goes black instead of giving me a login screen during boot and I need to revert the xorg.conf and boot again.
I've tried a combination of using a seperate X screen on each, to twin view on each card/Xinerama etc etc...
   If I use the latest Nvidia drivers "Version current" in Ubuntu which I Think is the 195 driver It only recognises the 8500 graphics card and doesn't load the 5500

The Nvidia site lists that the 5500 card is supported in the 195 driver here: [http://www.nvidia.com/object/linux-display-ia32-195.36.24.html](http://www.nvidia.com/object/linux-display-ia32-195.36.24.html)

The readme for the driver mentions a known problem with multicard setups here: [http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/knownissues.html](http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/knownissues.html)
 and I've added  Option "UseInt10Module" "True" to the Section"Device" for both cards in Xorg.conf but this doesn't seem to make a difference - only one card is shown in Nvidia X Server Settings.
If I try to install the latest Nvidia drivers available on that site it mentions that my card isn't supported in this driver and I need to use an older one - which is strange as the supported driver list on the readme says it is!  I also found this page:
 [http://www.gentoo.org/doc/en/nvidia-guide.xml](http://www.gentoo.org/doc/en/nvidia-guide.xml)
 which mentions that FX 5 series cards should use the 173 driver, but I can't configure it to allow multi monitor across both cards.

Is there any way to run 2 seperate Nvidia drivers? - one for each Graphics card? - or is there something else I'm missing that might help?

---

### Post by elialbert on 2010-09-18
i'm having a very similar problem with one 5200 and one 6200 in the same box on ubuntu 10.04. i can configure them perfectly well in the nvidia-settings tool, both are recognized with all four monitors, i save the new xorg.conf file and i've reviewed it and it looks great, and then when i restart, although all 4 monitors get green lights, the computer freezes - i get a black screen, although at one point screen 1 had a movable mouse. no keyboard command can get me out of the frozen state.

help?!

---

### Post by danmarsden on 2010-09-19
no luck for me on this either - it's almost tempting to go back to windows as I know it works!

---

### Post by elialbert on 2010-09-19
yeah i don't have that choice, it's for my lab. i'll figure it out eventually and post here, but i'm guessing my solution will have to do with older/different proprietary nvidia drivers or even maybe the foss one (nouveau?).
then i get to do the same exact situation all over again on a different system with 2 ati cards.

---

