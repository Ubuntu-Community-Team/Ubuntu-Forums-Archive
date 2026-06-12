---
title: "Ubuntu 16.04 hybrid graphics cards AMD APU+ AMD GPU"
date: 2016-11-04
forum: Hardware
---

### Post by cyberdevoper on 2016-11-04
Hi

I am using Ubuntu 16.04 with opensource graphics drivers.Now what i am interested to do is to automatically switch whole graphics rendering to discrete GPU,instead of having integrated GPU running all the time and discrete GPU only if specific app requires one.

running inxi -G gives
[B]Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Richland [Radeon HD 8610G]
           Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265]
           Display Server: X.Org 1.18.4 drivers: ati,radeon,amdgpu (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on AMD ARUBA (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0[/B]

Running sudo cat /sys/kernel/debug/vgaswitcheroo/switch was giving
[B]0:IGD:+:Pwr:0000:00:01.0
1:DIS: :DynOff:0000:01:00.0[/B]
Once this command was edited in grub and update done
sudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" replaced with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.runpm=0"
output
[B]0:DIS: :DynOff:0000:01:00.0
1:IGD:+:Pwr:0000:00:01.0[/B]
Now i tried to add commands to /etc/rc.local since i know that x server needs to restart if you want to save the changes and run them but nothing changes.

I tried adding 
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
Still no luck.

I am running HP Pavilion 17 inch laptop with AMD Quad-Core A10-5745M APU and AMD A76M FCH

[http://support.hp.com/us-en/product/HP-Pavilion-17-Notebook-PC-series/7234909/model/7492687/document/c04471428/](http://support.hp.com/us-en/product/HP-Pavilion-17-Notebook-PC-series/7234909/model/7492687/document/c04471428/)

Now is there something that i am missing or i simply doing wrong?

PS:
CPU should be able to be overclocked to 2 more states(2.6GHz to all 4 cores and 2.9GHz 2 cores)but this is not possible due to BIOS being locked down and AMD overdrive tool not being made for GNU&linux distros.

Any advise on this one?

---

