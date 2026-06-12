---
title: "HIS HD 4350 iFan Native HDMI 512MB (64bit) DDR3 AGP"
date: 2011-06-08
forum: Hardware
---

### Post by drthrd on 2011-06-08
I have tried to install drivers for this card lots of times. I have tried AMD's drivers and the Ubuntu drivers. Every time I install the drivers when X starts it goes through my monitor ports (VGA, DVI, HDMI) then goes blank. I have tried several versions of AMD's drivers and the same thing happens. I looked at my Xor config file and fount this

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"

Should the BusID  be PCI or AGP? 

I looked at the Release Notes for AMD Catalyst™ 11.5 Proprietary Linux x86 Display Driver at [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx). In the Release Notes it says
> Note: If a Linux 2.6.11 or newer kernel was built with 
CONFIG_AGP enabled, the kernel AGP frontend is required to load 
the fglrx kernel module. To identify whether your kernel was built 
with CONFIG_AGP enabled, look for CONFIG_AGP=y in the 
kernel config file, or if the 'agpgart' module is loaded. Because my card is a AGP card is that is what causing the problems or is it something different? Has anyone gotten this card to work? How do I see if the agpgart module is loaded? Any help much appreciated.

---

### Post by drthrd on 2011-06-15
Nothing? What more information do you want?

---

