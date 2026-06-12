---
title: "ATI Radeon 9200 Direct Rendering and 3D acceleration issues"
date: 2009-02-27
forum: Hardware
---

### Post by bnc9 on 2009-02-27
I have been trying to get 3D accelaration (is it even possible on linux for my card?) and direct rendering to work on my Radeon 9200 gfx card but nothing I do seems to work. 
glxinfo | grep "direct rendering" Returns NO.

glxinfo | grep vendor returns:

```
server glx vendor string: Brian Paul
client glx vendor string: Brian Paul
OpenGL vendor string: Brian Paul
```
Is that even normal?... So I tried editing my xorg.conf to change drivers to the open source ones (the module name is ati) but no luck. Then I tried downloading the older proprietary drivers,because my card isn't supported in the latest releases, from the ati website but I the only drivers there are .rpm and I'm hesitant to install those (with alien).

lshw returns:
 ```
*-display UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8

```
 So my chip is not detected ? If theres anyone out there who has managed to get direct rendering with a Radeon 9200 (or an ATI chip as old as mine) can you give me a simple step by step How TO help me out?? GL based games that should work at full speed on my computer barely run....:cry:

P.S : I'm running 8.04 Hardy Heron

---

### Post by overdrank on 2009-02-27
Hi and I have a ATI 7500 on a laptop with Hardy and it works well with the driver from the install. I do not play games on it but compiz works well. Have you tried booting into recovery mode and use the xfix option to correct the graphics.
Recovery mode is usually the second choice from the grub when booting. Then you should be given 4 choices and the last is xfix. After completing the xfix you should be given the 4 choices again and one is boot normally.

---

### Post by bnc9 on 2009-02-27
I rebooted and ran xfix it overwrote my xorg.conf but
glxinfo | grep "direct rendering" still returns negative

---

### Post by overdrank on 2009-02-27
> **bnc9 said:**
> I rebooted and ran xfix it overwrote my xorg.conf but
glxinfo | grep "direct rendering" still returns negative

Ok you can use the command 
Edit using the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` to see which driver is being used. I am using the ati driver on the laptop.

---

### Post by bnc9 on 2009-02-27
k.. now I feel like an idiot... turns out my version of mesa messed things up so I installed a previous version (mesa-7.0) and presto! problem solved thnx for the help overdrank:KS!!

---

