---
title: "Ubuntu 11.04 sandy bridge support"
date: 2011-08-03
forum: Hardware
---

### Post by razorxpress on 2011-08-03
We all were disappointed with the current release of Ubuntu (11.04), that did not support sandy bridge processors. Though it was said it did, but many experienced locked boot(black screen due to graphics problem), continuous fan running problem in laptops and many more. Even if we even managed to boot, the graphics was glitchy and bad. We could not play any 3D games and run 3D super smoothly. Now things have changed with the release xorg drivers and kernel 3.0 final release. If you are installing Ubuntu in a sandy bridge processors these steps might help you. We all are waiting for OpenGL 3 to be implemented completely in mesa, hope it will happen next year.

Step 1 : Black screen of death at boot.

Before booting you will have access to grub menu. There is a line for linux kernel. Add following text after "quiet splash"

acpi_osi=linux pci=noacpi

This will solve the problem temporarily. 

Warning : In kernel line don't remove ro(read only). Don't omit anything from the kernel line. Only insert above text in respective place.

For permanent change modify "/etc/default/grub" as follows

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux pci=noacpi"

After making the change to that line issue following command

$ sudo update-grub

There are many options regarding acpi. If nothing works "acpi=off" is the killer one, but it will disable any power management support (battery, fan enabling feature).

Step 2 : Fan continuously running

Install a program called "lm-sensors" (search lm-sensors in synaptic and install)

After installation, from terminal issue following command

$ sudo sensors-detect

Answer YES to all questions. Specially the last one when it says it will add the line to "/etc/modules"

After the steps finished, check "/etc/modules" for the inclusion of your findings.

In my case lm-sensors found 

#----cut here----
# Chip drivers
coretemp
#----cut here----

Bottom of /etc/modules looked like this.

```

# Chip drivers
coretemp

```

After reboot you may check if the module has been loaded to kernel or not by using following command

$ lsmod | grep coretemp

or simply

$ lsmod

and see if the list contains the modules you loaded or not.

Step 3: Bad graphics

Propitiatory drivers for ati did not install (segmentation fault), so I had to rely on mesa, which did not support 3D quite well. With the release of xorg 1.7.6+4 it has improved. So I recommend to do a system update. If you don't want to update whole system, you still can update only the graphics driver by searching xorg in synaptic and updating all of the installed xserver* and xorg itself. Even after updating these drivers your computer will not support 3D as it is supposed to. Since graphics system in Linux is linked with kernel too, you have to update kernel 3.0 for 3D support. 

Ubuntu has not yet released update for kernel 3.0 as default for 11.04, so either you have to ask someone from ubuntu to do that, install 11.10, compile the kernel yourself(not recommended) or the most natural way download it from mainline oneric update. For that go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/) and downloaded the version that fits your computer. I mean 32-bit or 64-bit.

For 64-bit I downloaded 

linux-headers-3.0.0-0300_3.0.0-0300.201107220917_all.deb
linux-headers-3.0.0-0300-generic_3.0.0-0300.201107220917_amd64.deb
linux-image-3.0.0-0300-generic_3.0.0-0300.201107220917_amd64.deb

Install in order. If you want to install them via command line you may install gdebi-core

$ sudo apt-get install gdebi-core

and later run

sudo gdebi linux-headers-3.0.0-0300_3.0.0-0300.201107220917_all.deb

I did not do it via GUI (sorry for that). The last package (linux-image) should issue the update-grub command. If you don't see listing for 3.0 kernel at grub while booting (after you have installed these packages, recheck from synaptic), run sudo update-grub at terminal.

Conclusion: If you boot to the new kernel after graphics update you should see a performance improvement in graphics. To check if it really happened or not, you may install simple game like supertuxkart and check them on both kernels. I found glitches and lock in 2.6-8 or 10 while playing with minimum settings. In 3.0 I could play in full screen with full GUI enabled without any issue.

Issues : One issue I find with the kernel 3.0 is that it is not as quiet as 2.6.38-8 or 2.6.38-10 in terms of fan, but graphics is good. My advice would be to keep both and switch (3.0 for 3D games and 2.6-38-8 for normal work) if you are too cautious about heat, wait until ubuntu releases 3.0 kernel for current release.

---

### Post by dewapur on 2011-08-13
I see.. so the problem is because it doesn't support sandy bridge yet. I tried to install with Natty 64bit and grub menu was in text mode and it went black screen when trying to boot. I tried to boot Live-USB with 10.04.2 32bit and it went smooth until end of the process. So is it means Lucid have more support to sandy bridge processors?

---

### Post by sbraz on 2011-08-14
we're trying to address more problems here about sandy bridge here:
[http://ubuntuforums.org/showthread.php?t=1822629](http://ubuntuforums.org/showthread.php?t=1822629)

we're working to confirm a possible kernel bug and on a temporary fix.

---

### Post by Rob__oo00T on 2011-09-05
All,
i'm just check my 64bit 11.04 build with supertuxkart game (benchmark) , to confirm my suspects about problem with Sandy Bridge driver, and with big surprise I did not found glitches and lock as rasorexpress report, however I read that Sandy bridge support will be on next 11.10 Oneric that will be priveded with specific kernel 3.0.

May be recent Xorg updated can fixed rasorexpress issue reporter last July?

Rob

---

### Post by razorxpress on 2011-09-15
Yes, indeed it solved a lots of graphics problems. However, all the kernels above 2.38 has power regression problem as reported in many places. Still if I have to run some high graphics demanding games it requires me to load some of 3.0 kernels. Ubuntu 11.10 will have kernel 3, but due to power regression problem still to be solved, I doubt battery will last as long as it did in 2.38 and will have no heating problem. I think if the problem persists, I will have to use 2.38 kernel even in Ubuntu 11.10.

---

### Post by Rob__oo00T on 2011-09-15
Thanks razorxpress
fortunatly, I use Ubuntu on desktop pc and not on laptop device, maybe I will able to upgrade to 11.10 without thinking about battery issue.

I hope that power consuming issue will be fix soon.

Rob

---

### Post by rtalcott on 2012-02-25
Thank You!  Black screen is now gone!

---

