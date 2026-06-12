---
title: "Acer 3830TG Nvidia-prime/setup issues"
date: 2014-04-28
forum: Hardware
---

### Post by Chris_Sanders on 2014-04-28
I am new to the forums and am in need of help with an issue that I am experincing with with the setup and configuration of the nvidia drivers and nvidia prime. I use the Additional Drivers program included in Ubuntu to attempt to install the driver for my graphics card. The process completes seemingly fine I reboot and have no options for configuration inside the nvidia control pannel (*the only options availble to me are application profiles and nvidia-settings configuration)*. I run sudo lshw -c video and receive a responce of:  
*-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128) memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:4000(size=64)
With this responce I am lead to believe that the nvidia driver has not properly installed. When I execute the nvidia control pannel from terminal I receive the a message "** Message: PRIME: is it supported? no" where as this message makes me believe that. Of what I have been able to understand about Nvidia prime it is the Ubuntu version of what I have access to in Windows 7 of Optimus.
I have also tryed installing the correct version of the nvidia-settings manually in terminal for the driver which the one I am using is the nvidia propriatary 331 driver on ubuntu 14.04.
My questions are 1. how can I get the driver to properly install? and 2. how can I get the Nvidia prime funtionality to work after I get the driver working?
I do realize that Prime does not allow the same funtionality as Optimus in Win7 yet the ability to select a graphics card is something I greatly desire to optimize battery life when spending long periods of time away from a charger.
 [ATTACH=CONFIG]252595[/ATTACH]
I have included a image to show that I am seeing. Any help will be greatly appreciated!

**edit
I forgot to explain that I have tried to use the the command nvidia-xconfig and receive a responce that it is an invalid command.

---

### Post by Chris_Sanders on 2014-04-29
Any suggestions at all? :confused:

---

### Post by Chris_Sanders on 2014-04-29
Nothing???

---

### Post by Chris_Sanders on 2014-05-01
Still hoping for assistance or suggestions for this issue.

---

### Post by Chris_Sanders on 2014-05-12
Is there no ideas on this at all? Is there a known issue that I have yet to find?

---

