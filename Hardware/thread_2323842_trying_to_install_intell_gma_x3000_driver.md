---
title: "trying to install intell gma x3000 driver"
date: 2016-05-08
forum: Hardware
---

### Post by jgw on 2016-05-08
I have been trying to install the driver for intel video on motherboard.  I am running with 14.04.3   I have tried a number of things to no avail.  The latest was 

sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libqt5gui5 libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386 libglapi-mesa-lts-utopic:i386 libegl1-mesa-drivers-lts-utopic

Which, in theory installs everything in one fell swoop.  It seemed to fun fine but no driver.  I also went to see if there were any available additional drivers (there were not).

Then, again, I may be just fine. 
 
lshw -c video returned:
-display               
       description: VGA compatible controller
       product: 82G965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:90300000-903fffff memory:80000000-8fffffff ioport:2140(size=8)

My display only shows 1 available display: 1024x768  Should I have more?  I am running with a 23" display.

---

### Post by him610 on 2016-05-08
I assume you have an intel GFX chip on your motherboard, and a GeForce 8600 GT GFX card installed in one of your PCIe slots. Is that correct?

It is my experience that the choice between onboard GFX chip and in-the-slot GFX card is made in your BIOS. If you have chosen to boot with the GeForce 8600 GT, the driver for your onboard intel chip will not be loaded because it is not necessary. (If I am mistaken, hopefully, someone will jump in to provide the correct information) 

Fixing the issue of your resolution is another issue. It can be corrected.

---

### Post by mörgæs on 2016-05-09
If you want new drivers then best you can do is to begin with a fresh install of 16.04 rather than 14.04. 

Is the Nvidia mentioned in your footnote part of the hardware?

---

### Post by jgw on 2016-05-17
I found I have a  Intel Corporation 82G965 Integrated Graphics Controller.  I then went to the intel site and checked for their latest and greatest linux driver.  It seems that Ubuntu 14.04.3 has installed the correct driver and everything is dandy and I have, yet again, asked a question I should have known the answer to.  I will mark this as done.

---

