---
title: "Dell XPS M1710 video issues Maverick"
date: 2011-08-02
forum: Hardware
---

### Post by Holker on 2011-08-02
Hiya,
I am new to this, so hopefully someone can help me out here.
I just have installed Ubuntu Netbook 10.10 Maverick (didnt like 11.04 yet, sorry) on my Dell XPS M1710 laptop and I think my NVidia GeForce Go 7950 GTX videocard isnt working properly. I have selected and activated the recommended NVidia driver, but I still cannot start up wobbly windows, compiz cube, etc., when I left click the background. The option to it is grayed out. Also video's are difficult to watch in fullscreen (top half is in next image, when bottom half is still in the previous image). Can someone help me out please? :confused:

---

### Post by Holker on 2011-08-03
Can no one tell me how to install the correct video driver?
Should I maybe post this in the absolute beginner forum?

---

### Post by Holker on 2011-08-04
Little update; I have changed the NVidia X Server Display Configuration Settings to 1920x1200 and 60Hz plus slided the OpenGL Image Settings to High Quality and this seems to help a little bit with the videos. Also I have installed Compiz, which enabled the Visual Effects, however I cannot use them yet, because of the driver.

I have been looking around in the forum and found some Nouveau stuff for advanced users (not sure if I should use this guide) and NVidia posts, but confused me only more. In one post I found some command for more info and used it:
```
sudo lshw -C display; lsb_release -a
[sudo] password for holker: 
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce Go 7950 GTX]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff ioport:ef00(size=128) memory:efe00000-efe1ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```I also went to the NVidia website and downloaded the NVIDIA-Linux-x86-280.13.run file for my GeForce Go 7950 GTX driver, but I have no clue how to use this file. Can someone help me out with this please? Thank you in advance.

---

