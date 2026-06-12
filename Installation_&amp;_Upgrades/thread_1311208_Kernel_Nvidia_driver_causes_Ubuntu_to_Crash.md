---
title: "Kernel Nvidia driver causes Ubuntu to Crash"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by nixed242 on 2009-11-02
I've been trying to get Karmic Koala to boot correctly for a few days now. The Live CD didn't work, and the Alternate CD installed for me, but I can't use Gnome/X unless I boot into recovery mode and launch GDM from a command line (not the most stable way to run Ubuntu). 

I narrowed down the problem to the NVIDIA Driver/Module that the kernel loads on boot. If I can bypass this driver and get the Kernel to load a VESA driver instead, I think the problem will be solved. I tried removing all of the NVIDIA drivers using synaptic. Upon reboot I was able to get a command line login prompt instead of the graphical GDM interface that Karmic uses. However, I was unable to log in because my screen kept flickering. 

Is there a way to remove the NVIDIA driver from my Kernel and force it to use VESA on start without having to recompile the Kernel? I tried using the dkms command line options to no avail. The Ubuntu Installer by default detects my NVIDIA card and compiles the driver into the kernel. There's no way I know of to prevent it from doing so during install. Any help with this would be greatly appreciated! There are several people in the forums with a similar issue. 

My computer specs are: 
[B]Processor: AMD Athlon 64, 2000 MHz 3200+
Motherboard: FIC KT800-T
RAM: 1536 MB (PC3200 DDR SDRAM)
Graphics card: NVIDIA GeForce 7600 GT (512 MB)
Tried installing all flavors of 32 bit and 64 bit Karmic Koala[/B]

Thanks,
Nixed

---

### Post by trebach on 2009-11-02
Try editing /etc/X11/xorg.conf in recovery mode and changing the line
```
Driver "nVidia"
``` to
```
Driver "vesa"
```

---

### Post by nixed242 on 2009-11-02
Thanks, I'll give it a shot, but X works fine using the NVIDIA driver when I load it in Recovery mode. I believe the problem lies when the nvidia driver is called from the Kernel. Doesn't Ubuntu 9.10 call  the video driver from the Kernel Module so it can load the graphical boot and login screen?

---

### Post by nixed242 on 2009-11-03
As I just posted to Ubuntu Bug Report Launchpad - 

I solved the problem! The issue wasn't with the NVIDIA driver at all. My FIC KT800 motherboard contains VIA chips, which are buggy with Ubuntu. To get it to work, I would have to turn off ACPI in my bios since the "acpi=off" parameter wouldn't do anything at boot time. The 9.10 Live CD, and the Alternate Install CD, load ACPI as a Runlevel 2 3 4 and 5 script. This was what caused my system to hang during normal boot. Of course, recovery mode has a Runlevel of S which doesn't run the ACPI script.

To remedy the issue, I went into /etc/rc2.d from Recovery mode and renamed "S99acpi-support" to "K99acpi-support" and that fixed things. Now I also renamed "S99laptop-mode" and "S99ondemand" just to be sure, and have since not named them back. I'm sure if I do, everything would work still as long as "acpi-support" is not loaded. I don't even know why "S99laptop-mode" script is in there since I'm running Ubuntu on a Desktop!

But in all fairness, and where criticism is due, why would an Alternate Installer, install the ACPI script, when at least 15% of the people trying Ubuntu have a buggy chipset that cause it to crash with ACPI? I thought the whole point of the Alternate Installer was to allow people to install the system with safe drivers? I would hope Ubuntu would omit the ACPI script from the Alternate Install in the future. I'm sure it would solve have of the help requests in the forums.

---

