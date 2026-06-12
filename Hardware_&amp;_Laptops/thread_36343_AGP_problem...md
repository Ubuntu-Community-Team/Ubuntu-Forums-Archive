---
title: "AGP problem.."
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by teme82 on 2005-05-23
Hi!
I have  nvidia Fx 5200 card and it should bee in AGP 8X mode, but the nvidia-settings tells me it's in PCI mode.

here all what dmesg tells about agpgart:

agpgart: Detected SiS 746 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xd0000000

at th end nvidia driver tells me this :

NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
NVRM: not using NVAGP, an AGPGART backend is loaded!
NVRM: not using NVAGP, an AGPGART backend is loaded!

---

### Post by ubuntuwow on 2005-05-23
you know what, there must be some problems with having integrated video cards like intel845, and an extra agp/pci video card. the agpgart probably has to do with a built-in video card. atleast you're comp boots. i have a pci video card along with a integrated agpgart, and my linux wont boot with the pci one in. sorry, i can't help you specifically with this, hopefully someone else can.

---

### Post by teme82 on 2005-05-23
[QUOTE=ubuntuwow]you know what, there must be some problems with having integrated video cards like intel845, and an extra agp/pci video card. the agpgart probably has to do with a built-in video card. atleast you're comp boots. i have a pci video card along with a integrated agpgart, and my linux wont boot with the pci one in. sorry, i can't help you specifically with this, hopefully someone else can.[/QUOTE]

I don't have any integated video card. So mystery still goes on :P
I did cat /proc/driver/nvidia/agp/status

Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file

---

### Post by Rodrigo on 2005-05-23
I have kind of a same problem with and old nvidia TNT2 Model 64 pro (or something like that  :razz: )
It tells me that its pci, and it should say agp... weird  :roll: , well at least it works... kind of.... the other problem its that its a 32 MB card, and it says its an 16 MB card  :mad: 
Some one knows how to fix this?

---

### Post by farnsworth on 2005-05-23
you might want to try this:

~$ lsmod | grep -i agp

you should see 'agpgart  [some number]   nvidia'

if not, agpgart might be using another module for video.  when I had this problem, I had to blacklist the offending module (add module name to /etc/hotplug/blacklist file) and explicitly tell Xorg to use nvidia AGP (add >{Option  "NvAGP"  "1"}< to /etc/X11/xorg.conf)

I hope that helps.

---

### Post by teme82 on 2005-05-24
[QUOTE=farnsworth]you might want to try this:

~$ lsmod | grep -i agp

you should see 'agpgart  [some number]   nvidia'

if not, agpgart might be using another module for video.  when I had this problem, I had to blacklist the offending module (add module name to /etc/hotplug/blacklist file) and explicitly tell Xorg to use nvidia AGP (add >{Option  "NvAGP"  "1"}< to /etc/X11/xorg.conf)

I hope that helps.[/QUOTE]

It was fixed when I add these lines,
to xorg.conf :
"NvAGP" "3"

and to modules
nvidia NVreg_EnableAGPSBA=0 NVreg_EnableAGPFW=1

now /proc/driver/nvidia/status looks like this:
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

---

### Post by poofyhairguy on 2005-05-24
can you make a how to for this....please?

---

