---
title: "can't choose a monitor"
date: 2008-07-27
forum: General Help
---

### Post by noiseblast on 2008-07-27
I have a strange problem. I'm trying to choose a monitor, so that I can change the resolution. I also have an nVidia graphics card, but that is a different matter. 

The thing that I'm trying to do is run the sudo dpkg-reconfigure -phigh xserver-xorg command in terminal. When I had ubuntu installed previously (same version) it worked fine and I could access the monitor options when I restarted after writing the dpkg- reconfigure command.

This is the message that appears in terminal when I'm trying the dpkg-reconfigure command now.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080727162958

What's wrong?

---

### Post by northern lights on 2008-07-27
> **noiseblast said:**
> sudo dpkg-reconfigure [COLOR="Red"]-phigh[/COLOR] xserver-xorg
The 'p*value*' flag sets the minimum priority of questions that will be displayed. Apparently, there are no high priority questions when reconfiguring 'xserver-xorg', so it doesn't ask you any.

Run it without '-phigh' to be asked some. Not too certain it's gonna ask you about a monitor, though.

As for the actual problem with the resolution, can you post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by noiseblast on 2008-07-27
Thanks for a quick response.

the output of sudo lshw -C display looks like this:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: G72 [GeForce 7500 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0


I tried the dpkg reconfigure without -phig and it got me where I wanted, but even though I managed to choose a monitor there, it didn't work.

---

### Post by northern lights on 2008-07-27
The device drivers are not set up right, your running under VESA.

Navigate to "System > Administartion > Hardware Drivers". Can you activate 'NVIDIA accelerated graphics driver'?

---

### Post by noiseblast on 2008-07-27
Thanks!

Now I can get the correct resolution and everything looks normal.

The sudo lshw -C display now looks like this:

 *-display               
       description: VGA compatible controller
       product: G72 [GeForce 7500 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by northern lights on 2008-07-27
> **noiseblast said:**
> 
 *-display [COLOR="Red"]here it formerly read UNCLAIMED (no driver)[/COLOR]              
       description: VGA compatible controller
       product: G72 [GeForce 7500 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: [COLOR="SeaGreen"]driver=nvidia[/COLOR] latency=0 module=nvidia

Green marks the new driver. Sorted.

---

