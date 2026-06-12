---
title: "Dual Monitors with Dell PR03x Docking Station (Bad to worse)"
date: 2013-12-02
forum: Hardware
---

### Post by washad2 on 2013-12-02
Proud to have moved to Kubuntu for my base OS for work (Using VMs for Windows stuff) over the weekend. But I've came into work, plugged into the docking station, and the troubles have begun. 

I started by being able to display both monitors - but they were mirrored and the behavior was erratic (multiple mouse pointers, screen not refreshing). I thought I'd be clever and install proprietary NVidia drivers. That made things worse as I could lo longer get any monitors via the docking station. I tried removing the nvidia drivers to no avail. 

Currently, I am stuck with a single monitor and out of options. 

Can anyone offer any help?


System: Dell Latitude, Kubuntu 13.10, Dock PR03X

Thank you, 

SteveJ

---

### Post by Bucky Ball on 2013-12-02
Can you see the second monitor in the Display settings? Have you tried playing around with arandr?

---

### Post by washad2 on 2013-12-02
> [COLOR=#000000]Can you see the second monitor in the Display settings? Have you tried playing around with arandr?[/COLOR]

Thank you for the reply; 

I cannot see the monitor in the display settings. I could at the start of the day, before the Nvidia mess, but I can't anymore. The additional monitors don't show in arandr either.

---

### Post by Bucky Ball on 2013-12-03
Do you have anything enabled in Additional Drivers?

Please give the output of:

```
sudo lshw -C video
```

---

### Post by ergosteur on 2013-12-05
Edit: Just noticed you're using NVIDIA graphics. we may have a different issue.

Also using a PR03X. My laptop is a Latitude E7420 with Intel HD Graphics 4400 I believe. lshw reports
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:65 memory:f7400000-f77fffff memory:e0000000-efffffff ioport:f000(size=64)

I can see the monitor in Screen/Display settings, it's enabled, but no picture. Monitor stays in standby.
Using an HDMI-DVI adapter to connect the monitor directly to the laptop's HDMI port works fine.

Running Ubuntu 13.10 64-bit installed in UEFI mode, secure boot on.

---

