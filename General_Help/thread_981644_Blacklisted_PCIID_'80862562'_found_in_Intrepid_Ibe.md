---
title: "Blacklisted PCIID '8086:2562' found in Intrepid Ibex"
date: 2008-11-13
forum: General Help
---

### Post by quantumboy85 on 2008-11-13
I have an on board Intel graphics card which worked with Compiz without any problems in Hardy Heron and previous versions but which is blacklisted in Intrepid Ibex. For the display, lshw lists:

```

 *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0


```

I've told Compiz to ignore the blacklist by following instructions [here]("http://ubuntuforums.org/showthread.php?t=765875"), but when I start Compiz, all panels and windows disappear; the mouse moves around but I can't even restart or kill X11. Running
```

compiz --replace &

```
gives
```

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```

I'm not sure if this problem is something that can be fixed, perhaps with another version of Compiz or something like that or why it would arise in the 1st place, as this driver had no problems at all in previous releases.

---

### Post by pluckypigeon on 2008-11-18
I have EXACTLY the same problem and have had it for ages now!! It's really annoying:confused:

---

### Post by pluckypigeon on 2008-11-18
This is a thread I started

[http://ubuntuforums.org/showthread.php?t=962520](http://ubuntuforums.org/showthread.php?t=962520)

As of yet, it hasn't solved my problem but I'll keep you updated!!

---

