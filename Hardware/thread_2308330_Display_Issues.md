---
title: "Display Issues"
date: 2016-01-02
forum: Hardware
---

### Post by cAlpha on 2016-01-02
Running Ubuntu 15.04 as part of a dual boot with Windows 7 and only one of my two monitors works while working within Ubuntu, though both work when working in Windows.  

My HDMI connection is the one causing issues and connecting to my TV via HDMI doesn't work at all either, so thinking it may be a simple driver issue.  

Any ideas?  My machine is an Asus B43S laptop with Intel i5-2520m processor.

---

### Post by cAlpha on 2016-01-02
++

---

### Post by cAlpha on 2016-01-03
++

---

### Post by mörgæs on 2016-01-04
How does it work in a live boot of 16.04 (development version)?

---

### Post by cAlpha on 2016-01-04
Not sure.  Would I need to create a boot disk to test this or is there an easier way?

---

### Post by mörgæs on 2016-01-04
Booting from USB is also an option.

---

### Post by cAlpha on 2016-01-04
something to consider.

any other thoughts about debugging the existing installation?

---

### Post by matt_symes on 2016-01-04
Hi

Are you using a custom xorg.conf file or relying on KMS to discover and configure your displays ?

Have you tried any custom xrandr commands ?

What have you tried ? Linux has been known to be problematic with mulitple monitors in the past.

With both monitors connected, can you post the output of this command ?

```
xrandr
```

Kind regards

---

### Post by cAlpha on 2016-01-04
thanks.  running mostly with the default installation at this point, but looks like I am relying on KMS (radeon kernel modesetting appears to be enabled, per dmesg).  wasn't familiar with KMS prior to your question, but it appears it may also explain why I get resolution quirkiness when the HDMI is plugged in (resolution of main monitor defaults to 1024:768 rather than the otherwise default 1920:1080).    

output of xrandr with both plugged in:
```

chris@chris-B43S:~$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.9  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
LVDS-1-1 disconnected
DisplayPort-1-3 disconnected
HDMI-1-3 disconnected
DVI-1-0 disconnected
VGA-1-1 disconnected

```

---

### Post by matt_symes on 2016-01-04
Hi

According to your post above, you have three connected displays. HDMI2, VGA1 and LVDS1. That would make this a three monitor display !

You may have better luck with a custom xorg.conf file.

For the moment, open a terminal and type this command.

```
xrandr --output HDMI2 --auto --primary
```

Do you get output to the TV ?

Kind regards

---

### Post by cAlpha on 2016-01-04
no output, but did get a 'mirrored displays' bubble that popped up in the upper left of the functioning monitor

---

### Post by matt_symes on 2016-01-04
Hi

> **cAlpha said:**
> no output, but did get a 'mirrored displays' bubble that popped up in the upper left of the functioning monitor

Has the HDMI output ever worked ? 

The HDMI2 output you posted from the xrandr command looks good, stating it's connected and it's the primary connection.

> HDMI2 connected primary

Can we check your logs next. Please post the output of this command. The capital letters below are important.

```
egrep "HDMI2|EE" /var/log/Xorg.0.log
```

Kind regards

---

### Post by cAlpha on 2016-01-04
yeah, the port and display work fine, just not when booted into ubuntu--if I'm logged into the windows side, second display and connection to TV work without issue.  otherwise, and I can't entirely recall if I had this issue, or even the dual displays, the last time I'd dual booted ubuntu a few years back, but suffice it to say I can't recall the dual displays ever working within ubuntu

output below:
```

chris@chris-B43S:~$ egrep "HDMI2|EE" /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    46.851] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    46.861] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    46.866] (II) intel(0): Output HDMI2 has no monitor section
[    46.866] (II) intel(0): Enabled output HDMI2
[    46.867] (--) intel(0): Output HDMI2 using initial mode 1920x1080 on pipe 1
[    46.985] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    47.137] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 1, position (0, 0), rotation normal, reflection none
[    54.558] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[    58.256] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[ 66111.415] (II) intel(0): switch to mode 1024x768@75.1 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 67727.626] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 67727.742] (II) intel(0): switch to mode 1024x768@70.1 on HDMI2, VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 67728.448] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 67770.431] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (1920, 0), rotation normal, reflection none
[ 67786.583] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 67847.478] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (1920, 0), rotation normal, reflection none
[ 67877.576] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 73114.109] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[ 73116.325] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2, VGA1 using pipe 0, position (0, 0), rotation normal, reflection none

```

---

### Post by matt_symes on 2016-01-04
Hi

Not much wrong with that grep log snippet either.

Don't take offense at this question if it seems too stupid but your monitor is definitely configured to accept input from the correct monitor HDMI port input ?

Also have you tried a different HDMI cable ?

Everything you have posted so far suggests that the HDMI monitor should be (and is) working.

Kind regards

---

### Post by cAlpha on 2016-01-04
Appreciate your help.  Yeah, there's no issue with the monitor or cord--of late I simply boot into windows anytime I need the second display or want to connect the TV.

You're not seeing anything indicative of driver issues?

---

### Post by matt_symes on 2016-01-05
Hi

> **cAlpha said:**
> Appreciate your help.  Yeah, there's no issue with the monitor or cord--of late I simply boot into windows anytime I need the second display or want to connect the TV.

You're not seeing anything indicative of driver issues?

I can see nothing at the moment.

You may want to post the entire */var/log/Xorg.0.log* file, maybe as an attachment if it very large, because that small grep we ran may have missed something like bad EDID information.

I can look later today for you.

Kind regards

---

### Post by cAlpha on 2016-01-05
log file attached 

[ATTACH]266558[/ATTACH]

---

### Post by matt_symes on 2016-01-05
Hi

Any reason you're using the open source Radeon driver and not fglrx ?

EDIT:

Actually it looks to be loading both the Intel driver and the Radeon driver.

Does your laptop have two graphics chips ? 

Can you post the output of this command

```
sudo lshw -C display
```

Capital C above.

Kind regards

---

### Post by cAlpha on 2016-01-05
no particular reason (I'm using one versus the fglrx) and only one graphics card as far as I know.

```

chris@chris-B43S:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:36 memory:f5000000-f53fffff memory:d0000000-dfffffff ioport:e000(size=64)

```

---

### Post by matt_symes on 2016-01-06
Hi

I'm really not sure what to suggest to be honest.

See if anybody else has some idea.

Kind regards

---

### Post by cAlpha on 2016-01-08
Fair enough...regarding the drivers, might changing my driver to fgrlx be useful and if so, how to switch?

Appreciate your help.

---

