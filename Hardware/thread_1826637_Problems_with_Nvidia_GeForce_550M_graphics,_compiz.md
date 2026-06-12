---
title: "Problems with Nvidia GeForce 550M graphics, compiz, and unity"
date: 2011-08-16
forum: Hardware
---

### Post by alas-poor-yorick on 2011-08-16
I just installed Natty on a new laptop, and I think it is having trouble with my video card (Nvidia GeForce 550M (switchable graphics with Optimus)). When I try to log in to Ubuntu (not Ubuntu Classic), it says "it seems that you do not have the hardware required to run unity". Also, there is no "effects" tab in appearance settings, and changes I make to compizconfig do not have any effect.

I added the ubuntu-x-swat/x-updates ppa and it says nvidia-current is at the latest version. I also tried downloading and installing the same version from the nvidia website. 

When I run nvidia-settings, it gives me an error message saying "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." When I run sudo nvidia-xconfig, it says:
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

And the computer ceases to boot into X until I restore xorg.conf.backup.

Here is the output of sudo lshw -C display:
```
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:2000(size=128) memory:f1000000-f107ffff
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
       resources: irq:52 memory:f1400000-f17fffff memory:e0000000-efffffff iopor
```

So it does recognize that the card exists, it just doesn't seem to be using it. System -> Administration -> Additional Drivers says the driver is "activated but not currently in use".

I don't know if this matters, but my computer has a physical switch to turn the GPU on and off. Turning it on means it (supposedly) uses Optimus and sometimes uses the GPU depending on what programs I'm running. In windows, there is a light that turns on when the switch is on. In Ubuntu, the light is always on and flipping the switch does not seem to do anything.

Does anyone know how to fix this?

Thank you

EDIT: just saw this post: [http://ubuntuforums.org/showthread.php?t=1790785](http://ubuntuforums.org/showthread.php?t=1790785)
I think this is a related but distinct issue - I can live without optimus/bumblebee working and switching properly, but I'd really like to be able to use compiz.

Edit 2: I tried the changes recommended in that thread and now not only does the computer not boot, but it doesn't display any text on the screen while it is not booting. It just shows a blank screen until I power it off.

---

### Post by sambarino on 2011-08-17
Hi yorick,

Unfortunately I can't help you here as I am suffering from an IDENTICAL problem, and I am in exactly the same state as you. If I delete my xorg.conf I boot in but the nVidia card is not being used.

I did have a look at something called bumblebee: [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee) but when I boot it fails to start so I'm not sure if it would fix the problem if it was working or if it's just another dead end.

But if I boot into "recovery" mode and choose "failsafe graphics" and then "run with low graphics for a single session" I can at least get into my normal login without deleting my xorg.conf 

I always run my notebook plugged-in so I wouldn't mind if I just used the nvidia card all the time, I wish there was a way to choose which card to use as default in the bios :(

---

### Post by TheMiz on 2011-08-17
I just want to chime in and say that I have the same problem with my Y470.

I have been running Ubuntu 11.04 with Unity, but I have presumably been using the Intel on-board graphics, and not the GeForce GT 550M.  Unity and Compiz seem to work okay as long as I resist the urge to try and install the nvidia drivers or the nouveau drivers.  I have even tried the 280.13 driver, but I have not had success.

There is a lot of discussion about this on the Lenovo forums as well, but noone has had success in getting it to work.

Have you guys had luck getting your USB3.0 ports on the left of the machine to work?

---

### Post by alas-poor-yorick on 2011-08-18
> **TheMiz said:**
> Have you guys had luck getting your USB3.0 ports on the left of the machine to work?

Mine didn't work the first time I installed it, but I did a fresh install and then they worked without me having to change anything. Not sure what changed.

---

### Post by sambarino on 2011-08-18
I think my ports working fine, I'm going to wait for the next stable release of bumblebee to see if it helps me.

---

### Post by nerdman978 on 2011-08-28
> **TheMiz said:**
> 
I have been running Ubuntu 11.04 with Unity, but I have presumably been using the Intel on-board graphics, and not the GeForce GT 550M.  Unity and Compiz seem to work okay as long as I resist the urge to try and install the nvidia drivers or the nouveau drivers.  I have even tried the 280.13 driver, but I have not had success.


Just out of curiosity, how were you able to get Unity and Compiz to work without the nvidia drivers? I have a Y570 with a Geforce GT 555M, and I've had no luck getting compiz or unity to work without the nvidia drivers (ignoring the fact that optimus doesn't work.. if I really need anything that graphically intensive I'll just boot to windows)

---

### Post by nerdman978 on 2011-08-28
Figured out that the problem was with having the nvidia drivers installed, and by removing the nvidia drivers the problem went away.

---

### Post by TheMiz on 2011-09-06
I currently have the nvidia drivers installed as part of the ironhide package.  ([https://github.com/MrMEEE/ironhide](https://github.com/MrMEEE/ironhide)).  As long as you do not have an xorg.conf file at /etc/X11/xorg.conf I have found that it will use the Intel graphics card.

I have not had a lot of great success with the ironhide package as a whole.

---

