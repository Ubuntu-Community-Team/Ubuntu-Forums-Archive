---
title: "Can't connect to tv via vga"
date: 2008-11-26
forum: Hardware
---

### Post by goathunter on 2008-11-26
hello. I am having a problem. When I boot with the vga plugged in my laptop screen goes blank, but does not show up on the lcd tv. When i plug in the vga when the laptop is already on nothing happens. I am using an acer aspire 3000 with a dedicated ubuntu 8.04. Its an amd mobile sempron with a VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter.
I have tried these commands but nothing happens.
Quote:
marcus@marcus-laptop:~$ xrandr --output LVDS --auto --output VGA --auto
marcus@marcus-laptop:~$ xrandr --output LVDS --auto --output VGA --auto
marcus@marcus-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
1024x768 60.0*
1024x576 60.0
960x600 60.0
960x540 60.0
800x600 60.0
768x576 60.0
720x576 60.0
856x480 60.0
848x480 60.0
800x480 60.0
720x480 61.0
640x480 60.0
640x400 72.0
512x384 60.0
400x300 60.0
320x240 61.0
320x200 71.0
marcus@marcus-laptop:~$ xrandr --output VGA --auto
I'm a bit out of my depth here so any help would be appreciated.

---

### Post by goathunter on 2008-12-02
bump

---

