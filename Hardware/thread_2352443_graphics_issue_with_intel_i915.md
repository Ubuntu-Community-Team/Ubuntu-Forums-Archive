---
title: "graphics issue with intel i915"
date: 2017-02-12
forum: Hardware
---

### Post by rebeltaz on 2017-02-12
So I am playing with makehuman and I am having trouble with the rendering engine. When I render the character, it comes out as a black shape. From makehuman - [http://www.makehumancommunity.org/wi...you_help_me%3F](http://www.makehumancommunity.org/wi...you_help_me%3F) - it's a problem with OpenGL. I can disable the shaders in makehuman, but is there anything I can do to Ubuntu 16.04 LTS to correct this in the OS?

    I've also noticed an issue with SketchUp under wine as well. If I [Save As] or [Export] the model area freezes up. The program still responds, but the model display area is no longer redrawn. If I minimize the window and then bring it back up, more times than not, the model display is black with what look like CRT retrace lines. I have to restart the program to regain control. I am thinking that these issues might be related? 


The video details are, if it helps:

```

derek@derek-home:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5050(size=8)

```

---

