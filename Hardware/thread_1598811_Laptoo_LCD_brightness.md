---
title: "Laptoo LCD brightness"
date: 2010-10-17
forum: Hardware
---

### Post by zhiyil on 2010-10-17
Hi,
This may be a bit long story. I have a Lenovo T410 laptop which was installed Ubuntu v10.4 (64-bit) when I got it. Things looked fine and smooth for one month. However, after using a projector via a VGA cable, I cannot turn my LCD brightness down and up by fn key plus down and up. And any projector or an external monitor cannot detect my laptop video signal either (I use fn+F7 to switch options). 

I read some threads in some forums and tried many things. This is what I tried:
- re-install xorg
- remove xconfig and let the system auto. set it up
- upgrade the system to Ubuntu 10.10

No approach is working so far. A funny thing is: when I deleted xconfig file, and a new one is created automatically by logging in again. Although the resolution is very low like 800x600, I can adjust brightness! You know, 800x600 is not an acceptable  resolution that I can use. So this is not a solution. 

This thread title may be misleading since my problem is not only with brightness adjustment but also projector detection,  i may also have other issues that I did not discover yet. 

When I go to the menu: System -> Preferences -> Monitors, a window shows that:

It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's  tool instead?

Then, yes, I got "NVIDIA server settings". By the way, I can adjust Brightness in this application. But this is not the way what I want and I could do when everything was okay initially.   

About my graph card: 
Graphics Processor:  NVS 3100M
CUDA cores: 16
VBIOS versions: 70.18.42.00.05
Memory: 256 MB
Memory interface: 64-bit
Bus type: PCI express x 16 Gen1
Bus ID: PCI:1:0:0
PCI Device ID: ...
PCI Vendor ID: ...
IRQ: 16
PCI-E max link speed: 2500
X screens: Screen 0
Display devices: LEN (DFP-0)
=====

I do not know what is wrong. :confused: My best guess is that Xorg looks okay, but the graphic driver, somehow, was destroyed. 

Any ideas/comments/solutions? Thank you in advance! 

Cheers,
Andy.

---

