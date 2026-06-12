---
title: "AMD RX5700 Dual Monitors, One Using an Incorrect Lower Resolurion"
date: 2019-12-29
forum: Hardware
---

### Post by Zoot_Nerper on 2019-12-29
I have a new setup with an AMD graphics card. I attach two 1920x1080 monitors, one via DVI and the other by HDMI. The latter does not have it’s native resolution of 1920x1080, but a lower one of 1024x768 (it used to be much lower at 858x480 when I first booted into Ubuntu).

In Ubuntu Settings&#8594;Devices&#8594;Screen Display the wayward monitor is identified as “Unknown Display”. The other is correctly identified.

I have a new install of Ubuntu 19.10, completely updated. I have not installed any additional graphics drivers. It is using AMDGPU, which is (I think) what it should be using.

Details of setup:

mainboard:       ASUS Prime x570-Pro
CPU:                 AMD Ryzen 5 3600X
GPU                  MSI Armor RX570 (1xDVI, 1xHDMI, 3xDP)
Memory:           32GB DDR4
Power Supply:   600W

Neither of my monitors support DP.

Using another computer and connecting the wayward monitor via HDMI (same cable), it uses and reports the correct native resolution.

Using a DP to HDMI cable from the RX5700 to the wayward monitor gives the same lower resolution.

I read that AMD only support LTS versions of Ubuntu, so I tried 18.04 via a Live USB. Same results.

If I connect the wayward monitor on its own via DVI it displays the correct resolution. (Unfortunately, I cannot just swap the cables and monitors as one monitor only supports DVI and the <wayward> one has DVI and HDMI.)

Some information from terminal commands:

xrandr reports:[INDENT]xxxxx:~$ xrandr
Screen 0: minimum 320 x 200, current 2944 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected 1024x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-D-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08 
[/INDENT]

---------------------------------------------------------------------

xxxxx:~$ sudo lspci -nnk | grep -i vga -A3 | grep 'in use'[INDENT][sudo] password for xxxx: 
    Kernel driver in use: amdgpu
[/INDENT]
 
---------------------------------------------------------------------

xxxxx:~$ sudo lshw -c video[INDENT]*-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:07:00.0
       version: ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:85 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fcf00000-fcf3ffff memory:fcf40000-fcf5ffff
[/INDENT]
 
---------------------------------------------------------------------

I also tried adding amdgpu.dc=0 to the kernel parameters to no effect.

I have been working on this for two days. I cannot find out if the MSI Armor RX5700 does or does not support DVI and HDMI working together. And obviously, I have not been able to resolve the situation myself.

Any ideas?

Thanks in advance.

-- Zoot

---

### Post by Yellow Pasque on 2019-12-30
Could we see a /var/log/Xorg.0.log ?

---

### Post by Zoot_Nerper on 2019-12-30
> **Yellow Pasque said:**
> Could we see a /var/log/Xorg.0.log ?

I have looked in /var/log and I do not have an Xorg.0.log. I only have the following log files in that directory:

[INDENT]/var/log$ ls *.log
alternatives.log  boot.log       fontconfig.log   ubuntu-advantage.log
apport.log        bootstrap.log  gpu-manager.log
auth.log          dpkg.log       kern.log
[/INDENT]


In case it may be relevant, I checked my Ubuntu login screen and I log into my username using Ubuntu not Ubuntu with Wayland.

-- Zoot

---

