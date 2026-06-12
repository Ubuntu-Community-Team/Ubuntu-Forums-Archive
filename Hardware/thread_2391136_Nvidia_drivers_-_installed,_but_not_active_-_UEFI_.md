---
title: "Nvidia drivers - installed, but not active - UEFI issue?"
date: 2018-05-06
forum: Hardware
---

### Post by endre on 2018-05-06
Everyone, it is good to be back again - 12 years since my first Ubuntu-installation, and after many years in Apple-land.

On installing 18.04 on my second hand Acer Aspire vn7 792G, I have run into one issue that I was hoping you all could help with.

I tried installing the necessary nvidia-drivers according to the instructions [found here]("http://https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux#h6-automatic-install-using-standard-ubuntu-repository") but at the end I am given an UEFI warning (which the instructions do not mention) saying that in order to activate my newly installed drivers, they need to be approved on reboot by a one-time password. I am also told that if I fail to do so, Ubuntu will reboot, but without the drivers being loaded. I create the password as requested in the UEFI dialogue, but when I reboot, I jump straight into the Ubuntu login screen without being given any chance to issue the password, and as warned, Ubuntu loads without the nvidia-drivers. The Software and Updates menu tells me they are installed, but the system clearly cannot communicate with them. When requesting system specs, I am told it can only find the integrated Intel 530 graphics, and not the GeForce 945M that I know is inside. In fact, when going into detailed system specs, I am just told that the graphics are "unknown".

So my question is - how do I get them activated? Should I remove and reinstall the drivers? Any way to provoke the UEFI dialogue again to fill in the right password? (Or is it possible I have been sold something claiming to have a screen card, when in fact it doesn't...)

Thanks!

EDIT: It seems like Ubuntu simply isn't recognizing the card (the Geforce 945M). Any tips on how to address this? Have tried re-installing the drivers to no avail.
[ATTACH=CONFIG]279601[/ATTACH]

EDIT 2: Another update - looks like Ubuntu insists on using whatever it has from Nvidia only as a "3D controller" while insisting that the Intel-graphics is its only VGA-controller.

sudo lshw -C display

  *-display                 
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:129 memory:63000000-63ffffff memory:50000000-5fffffff memory:60000000-61ffffff ioport:4000(size=128) memory:64000000-6407ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:125 memory:62000000-62ffffff memory:70000000-7fffffff ioport:5000(size=64) memory:c0000-dffff

---

