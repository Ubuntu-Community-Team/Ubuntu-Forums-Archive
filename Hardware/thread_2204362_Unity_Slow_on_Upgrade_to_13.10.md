---
title: "Unity Slow on Upgrade to 13.10"
date: 2014-02-08
forum: Hardware
---

### Post by linuxpyro on 2014-02-08
I just upgraded my laptop from 13.04 (64 bit) to 13.10 (also 64 bit), and now the desktop is extremely sluggish when using Unity.  I normally use a second monitor and figured that this may have been the problem, but even just using the laptop screen makes no difference.  This laptop has Intel Mobile 4 Series Chipset integrated graphics, and uses the i915 driver.  When I ran 13.04 it seemed a little sluggish, but nothing compared to this.  I'm using the fallback Gnome desktop (no effects) and it's tolerable, although I'd like to use Unity.  The fan in my laptop is running more often to, particularly when I was using Unity, although it still runs while using the fallback Gnome.  

Has anyone else had an issue like this?  I searched around and found mention of an issue with a mesa package from last year, which was supposedly fixed, but otherwise I haven't had any luck.

Here's my sudo lshw -c video output:
```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f4000000-f43fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4400000-f44fffff

```

And my /usr/lib/nux/unity_support_test -p output:
```

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits)
OpenGL version string:  2.1 Mesa 9.2.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

---

### Post by linuxpyro on 2014-02-08
Alright, looks like I actually fixed this, thanks to this thread:
[http://http://ubuntuforums.org/showthread.php?t=2182103]("http://http://ubuntuforums.org/showthread.php?t=2182103")
Turns out, I just had to run this, and select OK without changing anything on the screen that comes up:
```
sudo pam-auth-update --force
```

After that, the Unity 3D supported line in the unity_support_test -p output turned to yes, and the desktop is a lot better.  As a side note, I was having a Network Manager issue where connections I had set up prior to the upgrad were not showing up, and the Edit Connections... menu entry was grayed out.  This fixed that problem as well.

---

