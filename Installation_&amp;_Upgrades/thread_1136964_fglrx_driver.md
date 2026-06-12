---
title: "fglrx driver"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by uk1320 on 2009-04-25
When I attempt to upgrade from 8.10 to 9.04 I get a dialog box that says "This computer is currently using the AMD fglrx graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04. Do you want to continue?"

I responded "no" and exited the upgrade.

Does this mean I can't upgrade to 9.04?

---

### Post by El Cabrón on 2009-04-25
> **uk1320 said:**
> When I attempt to upgrade from 8.10 to 9.04 I get a dialog box that says "This computer is currently using the AMD fglrx graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04. Do you want to continue?"

I responded "no" and exited the upgrade.

Does this mean I can't upgrade to 9.04?


I have the same issue. 

ATI MOBILITY RADEON 9800
Proprietary Driver 8.54.3

I wonder if the message includes restricted drivers. That's where my confusion is. If not then I could upgrade and simply enable the restricted drivers for it but I don't know now. The warning is vague.

---

### Post by alphacrucis2 on 2009-04-25
> **El Cabrón said:**
> I have the same issue. 

ATI MOBILITY RADEON 9800
Proprietary Driver 8.54.3

I wonder if the message includes restricted drivers. That's where my confusion is. If not then I could upgrade and simply enable the restricted drivers for it but I don't know now. The warning is vague.

Jaunty comes with x.org server 1.6 which doesn't support the ATI Catalyst drivers prior to 9.4. The catch is that the fglrx(8.6) Catalyst 9.4 driver dropped support for a whole lot of older cards. If your card is one of those no longer supported then you can't use the proprietary driver with jaunty. You would have to use the open source ati or radeonhd driver. Which means that you will most likely lose performance and 3D support. ATI have realesed the documentation of the older cards but it will take probably some months before the open source ati driver developers get it all working.

---

### Post by El Cabrón on 2009-04-25
> **alphacrucis2 said:**
> Jaunty comes with x.org server 1.6 which doesn't support the ATI Catalyst drivers prior to 9.4. The catch is that the fglrx(8.6) Catalyst 9.4 driver dropped support for a whole lot of older cards. If your card is one of those no longer supported then you can't use the proprietary driver with jaunty. You would have to use the open source ati or radeonhd driver. Which means that you will most likely lose performance and 3D support. ATI have realesed the documentation of the older cards but it will take probably some months before the open source ati driver developers get it all working.


I guess this old Dell XPS PPO9L is just too old now.

---

### Post by hemna on 2009-04-25
I get the same dialog even thought I have an ATI Mobility X2300, which ATI says is supported by Catalyst 9.4

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf)

What gives?

---

### Post by simonpl on 2009-04-26
Looks like I lost support for my old X1300 :( hardly seems like last week to me that 512DDR2 and a nice clock speed were considered millennia in the future.

*reminisces his CGA and 300/300*.

---

### Post by uk1320 on 2009-04-26
It's not clear from these replies what will happen if I proceed with the upgrade - will the upgrade fail or will it install other drivers and work with reduced performance?

I will give it a go this evening and post the results here. Worst case scenario is that I have to re-install 8.10.

---

### Post by StuartN on 2009-04-26
> **uk1320 said:**
> It's not clear from these replies what will happen if I proceed with the upgrade - will the upgrade fail or will it install other drivers and work with reduced performance?

I will give it a go this evening and post the results here. Worst case scenario is that I have to re-install 8.10.

Run the Live CD and it will show you how your hardware will perform under 9.04. Run glxgears, put Compiz effects on and play some video in your current setting and under the Live CD to compare speed. lshw -C video will list the driver used in each setup.

---

### Post by El Cabrón on 2009-04-26
> **uk1320 said:**
> It's not clear from these replies what will happen if I proceed with the upgrade - will the upgrade fail or will it install other drivers and work with reduced performance?

I will give it a go this evening and post the results here. Worst case scenario is that I have to re-install 8.10.

If you upgrade you will not have 3d graphics, ability to run google earth or other programs that require it. You will be forced to use the free driver, which is 2d only. Maybe in a few months there will be support for the older cards... so someone says. Maybe... Either get a video card that is supported or don't upgrade. That's my option.

---

### Post by uk1320 on 2009-04-26
OK, I've done the upgrade with no dramas. I've played a couple of avi and mpg files OK.

The lshw -C video gives:

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress cap_list
       configuration: latency=0


I've not tried it with a live CD. The performance seems OK, but I've not even attempted to do any 3D stuff, no reason for me to do that as it's not something I normally do. I'm certainly not spending money on a new graphics card. This is only a secondary system, I usually use a Mac. Let the flames begin...

At least I know the system still works OK.

---

### Post by AZcat on 2009-04-26
My 6 year old PC has a Radeon 9700 pro graphic card installed.  Am running the 9.04 live CD with the visual effect set to extra.  Apps loading takes longer but that is to be expected.  Firefox actually runs faster once it is loaded than when it is running in 8.10.  Video works fine too.  Issued the lshw command while running a wmv file and got this response:

ubuntu@ubuntu:~$ lshw -C video
WARNING: you should run this program as super-user.
SCSI                      
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Radeon R300 ND [Radeon 9700 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R300 [Radeon 9700 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=32 mingnt=8
ubuntu@ubuntu:~$ 

Don't have 3D games to test the system.  So far everything seems to work okay.  Is there anything else I should test before going ahead with the upgrade?

---

