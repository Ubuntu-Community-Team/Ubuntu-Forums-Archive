---
title: "Increase resolution on my intel hd graphics 3000"
date: 2013-01-25
forum: Hardware
---

### Post by techfried on 2013-01-25
[LEFT][COLOR=#333333][FONT=Ubuntu Beta]I recently decided to go Ubuntu (12.10) on my laptop. Everything seems to be working fine but my screen resolution are set to 1366x768 and that's the maximum i can go.  I know i can go higher, i have intel hd graphics 3000 card on my dell inspiron n5110 15R laptop. Here's the lshw output.

[/FONT][/COLOR][/LEFT]
> $ sudo lshw -C video [sudo] password for techfried:    *-display                       description: VGA compatible controller        product: 2nd Generation Core Processor Family Integrated Graphics Controller        vendor: Intel Corporation        physical id: 2        bus info: pci@0000:00:02.0        version: 09        width: 64 bits        clock: 33MHz        capabilities: msi pm vga_controller bus_master cap_list rom        configuration: driver=i915 latency=0        resources: irq:57 memory:f6800000-f6bfffff memory:e0000000-efffffff ioport:f000(size=64)
[LEFT][COLOR=#333333][FONT=Ubuntu Beta]and here's xrandr output.

[/FONT][/COLOR][/LEFT]
> $ xrandr Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192 LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm    1366x768       60.0*+   40.1      1360x768       59.8     60.0      1024x768       60.0      800x600        60.3     56.2      640x480        59.9   VGA1 disconnected (normal left inverted right x axis y axis) HDMI1 disconnected (normal left inverted right x axis y axis) DP1 disconnected (normal left inverted right x axis y axis) 

[LEFT][COLOR=#333333][FONT=Ubuntu Beta]Can anyone help me increase my screen resolution to the max? Do I need to intall proprietary drivers? thanks[/FONT][/COLOR][/LEFT]

---

### Post by Grenage on 2013-01-25
Are you sure that's not the optimal resolution for the display? I would be surprised if it is not.

---

### Post by techfried on 2013-01-25
no i think it goes upto 1920x1080.

---

### Post by Grenage on 2013-01-25
I had a quick look on a spec sheet, and it did list the res you are getting as the standard res.  Perhaps I was looking at a different model, but that seems like an awfully high res for a small screen.

---

### Post by techfried on 2013-01-26
> **Grenage said:**
> I had a quick look on a spec sheet, and it did list the res you are getting as the standard res.  Perhaps I was looking at a different model, but that seems like an awfully high res for a small screen.

You are right. For some reasons i thought that my old windows 7 screen resolution is set to a higher screen resolution but it's not. I just switched to windows and checked that 1366x768 is the max i'm allowed to get. So perhaps I was wrong. But the window and icon sizes are pretty big in my ubuntu, i guess i need a different them to customize the desktop.
thanks guys.

---

