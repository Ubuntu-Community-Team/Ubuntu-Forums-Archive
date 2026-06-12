---
title: "Two screen Issues with Intel 945 GM"
date: 2011-02-07
forum: Hardware
---

### Post by crazy ivan on 2011-02-07
With my laptop intel 945 GM hardware accelaration works (compiz), even with a second monitor attached, when both are set to 1024 resolution. When I switch the attached monitor to native (higher) resolution two different scenarios occur:

* compiz enabled with various effects:
compiz crashes, both screens turns grey

* copmiz enabled, with few effects:
compiz crashes, may not be turned on afterwards, dual screens work

* compiz disabled:
dual screens work, compiz may not be turned on afterwards

Here is some output: 

lshw -C display
```

WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f4600000-f467ffff ioport:4000(size=8) memory:e0000000-efffffff memory:f4680000-f46bffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f4700000-f477ffff

```

---

### Post by crazy ivan on 2011-02-07
Hey there..

I have just run the marvellous compiz-check script from [forlong]("http://forlong.blogage.de/entries/pages/Compiz-Check"). And it told me a simple solution:

```

 ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2304x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).

```

It just seems that my second screen is 56 pixels too long!! Darn.. There must be a clever trick to compensate for that. Any ideas???

---

### Post by crazy ivan on 2011-02-15
Well there is.. Unfortunately the only option is having the screens share an overlap region. This is however pretty straightforward and described in
[this wiki]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things").

---

