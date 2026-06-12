---
title: "HP 300-019 HDMI video won't come back after display put to sleep"
date: 2016-03-30
forum: Hardware
---

### Post by stlu on 2016-03-30
Hello,

I'm in the process of trying out this little machine and one major problem is that the video signal won't come back after the display is put to sleep.  If I walk away for 20 minutes, come back, the display is off, and under normal conditions, I should be able to get the signal back by moving the mouse or pressing a key on the keyboard.  But nothing.  I can hit CTRL+ALT+F1 and get a text console, so the system is not frozen, merely tty7 is not able to restore the graphical session.

I can get a new graphical session by typing "sudo service lightdm restart".

```

$ sudo lshw -class video
[sudo] password for adam: 
  *-display               
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
       resources: irq:48 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)


```

---

