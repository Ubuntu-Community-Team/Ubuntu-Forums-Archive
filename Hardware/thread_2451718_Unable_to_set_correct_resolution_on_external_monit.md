---
title: "Unable to set correct resolution on external monitor"
date: 2020-10-09
forum: Hardware
---

### Post by skitter on 2020-10-09
I have a Lenovo LEGION 5 GeForce GTX 1660Ti Model 81Y6003YUS that I recently installed Ubuntu 20.04 on. I have a Acer H243H monitor connected to it via HDMI. Ubuntu lists the monitor unknown and will not allow me to set the resolution to 1920 x 1080.  The laptop display is detected and the resolution sets as expected. When the system is booted into Windows, the monitor is detected and runs at 1920 x 1080 Below are some commands I ran to try to see what the problem is, but I'm lost. Can someone lend a hand with getting the external monitor to run the 1920 x 1080 resolution?

```


skitter@laptop:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: TU116M [GeForce GTX 1660 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:160 memory:c5000000-c5ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:4000(size=128) memory:c4000000-c407ffff
  *-display
       description: VGA compatible controller
       product: UHD Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:144 memory:c3000000-c3ffffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff

skitter@laptop:~$ xrandr --listactivemonitors
Monitors: 2
 0: +*eDP-1-1 1920/344x1080/194+1600+0  eDP-1-1
 1: +HDMI-0 1600/423x900/238+0+140  HDMI-0


```

---

### Post by jfca283 on 2020-10-09
I installed pulse audio. On the mic option, I tried with 
[LIST]
[*]Default
[*]HDMI
[*]Analogue
[*]alsa_input.usb-Jieli_technology_USB_PHY_2.0-02.analog.mono
[/LIST]

Any of the options worked

---

### Post by skitter on 2020-10-10
The problem is seems to be the Acer H243H monitor itself.  I plugged that monitor into another PC running Ubuntu 18 and see the same issue where it's not detected, and I can't set the resolution to 1920 x 1080.  I attached an Asus monitor to the Lenovo running Ubuntu 20 and Asus is detected and works as expected. Really would like to get the Acer working on one of these machines.

---

### Post by ActionParsnip on 2020-10-11
It's probably not reporting EDID properly. If you use xrandr to add the resolution, does it help?

---

