---
title: "Graphic card Problem (Nvidia &gt; Intel)"
date: 2009-09-27
forum: Hardware
---

### Post by Gabtevez on 2009-09-27
Hi 

I have a big problem with my graphic card !!!! somebody help me please !!!

I have two Graphic cards 

1. **Nvidia 8500**
2. **Intel 82G33/G31** that became with my motherboard Intel 82G33/G31 Express

My problem is: 
I was using nvidia card and it run perfectly but yesterday I removed from my motherboard and select Intel card in BIOS. 

How can I select Intel graphic card driver in Ubuntut now because there is a lot of programs didn't work becasue my graphic card didn't work perfectly 

for example in TvTime program I face this error : 

> xvoutput: No XVIDEO port found which supports YUY2 images.and I can't use Compiz again . 

lshw output : 

> *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0

Xorg.conf :

> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Module"
    Load    "dri"
    Load    "GLcore"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "vesa"
EndSection

---

### Post by Gabtevez on 2009-09-30
anybody can help me please !!!!!!

---

