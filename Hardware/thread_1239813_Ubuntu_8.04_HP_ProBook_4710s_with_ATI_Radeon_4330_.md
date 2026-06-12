---
title: "Ubuntu 8.04 HP ProBook 4710s with ATI Radeon 4330 Graphics Card not seen by system"
date: 2009-08-13
forum: Hardware
---

### Post by bell1996 on 2009-08-13
I'm really hoping I get some much needed assistance here. I've been banging my head over this issue for a week. Ok here goes:

I just got a HP 4710s with a ATI Radeon Graphics card. I installed Ubuntu 8.04 and I'm very happy so far. Only problem is that the graphics card is not being recognized by the system. I'm not getting the full capabilities from it. The resolution is great (default to 1600x900) but it doesn't seem to know what driver to use. I've posted some of my out below. Please assist me. This is driving me crazy!!

sudo dmidecode -s system-product-name
HP ProBook 4710s
----------------------------------------------------------------------
lspci

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9552
01:00.1 Audio device: ATI Technologies Inc Unknown device aa38
03:00.0 Network controller: Intel Corporation Unknown device 4237
----------------------------------------------------------------------
*-pci:0
description: PCI bridge
product: Mobile 4 Series Chipset PCI Express Graphics Port
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 07
width: 32 bits
clock: 33MHz
capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-display UNCLAIMED
description: VGA compatible controller
product: ATI Technologies Inc
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list
configuration: latency=0
*-multimedia
description: Audio device
product: ATI Technologies Inc
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@0000:01:00.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
bell1996 is online now

---

### Post by bell1996 on 2009-08-14
Success!!!!

Just so you know what I did to make it work. So originally I was running 8.04 but ATI driver was not being recognized. Not able to get full functionality out of my graphics driver. I did many things while using 8.04 but was not successful.

So I did the following:

1) Upgraded to 8.10. This did not work either. Tried several things while using 8.10 but was not successful.

2) So, I upgraded to 9.04, thinking that something might make it work. Again nothing seemed to work.

3) Finally I had to RE_INSTALL 8.04. Not the best solution but I figured something was missing when I installed originally. 

4) After installing 8.04 I then immediatley went to [www.amd.com](www.amd.com) and downloaded the following application: ati-driver-installer-9-3-x86.x86_64.run

I followed the instructions and ran the ati driver installer & rebooted

After the reboot the system will ask you to enable the ati drivers. DON'T!! Just leave everything as is. I repeat DON'T enable the driver. 

That's it. Graphics card is enabled and able to use Compiz!

Hope this helps someone.

---

### Post by markbuntu on 2009-08-14
If you want to use jaunty, you can with the latest drivers from ati and that card. The driver in the jaunty repos does not work unless you get the updates first which is something that is not apparent since jockey offers the driver before update manager runs. Once again, do not install the driver offered, get the latest one from the ati site and make sure you have all the updates before installing it.

---

