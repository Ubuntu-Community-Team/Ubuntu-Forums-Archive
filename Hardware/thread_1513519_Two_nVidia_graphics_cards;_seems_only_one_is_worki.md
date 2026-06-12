---
title: "Two nVidia graphics cards; seems only one is working."
date: 2010-06-19
forum: Hardware
---

### Post by rawling on 2010-06-19
After upgrading (clean install) to 10.04 today, I finally found that I could use NVIDIA's drivers - they've never worked for me before, and although the "(version current) [Recommended]" ones still don't, the "(version 173)" ones do. Now I can have shiny visual effects and run World of Goo :D

I'm having less luck getting my second video card to work with my second monitor. The NVIDIA settings GUI only shows one screen and one GPU.

After some searching I discovered the nvidia-xconfig command (and to use it with gksudo). After looking at the switches I decided to try --enable-all-gpus ("Configure an X screen on every GPU in the system.") but this results in the following:

> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
WARNING: Unable to use the nvidia-cfg library to query NVIDIA hardware.


ERROR: Unable to determine number of GPUs in system; cannot honor
       '--enable-all-gpus' option..I tried --query-gpu-info ("Print information about all recognized NVIDIA GPUs in the system.") but that results in the same message, minus the file-writing parts.

I tried "opening" /dev/nvidia0 (in gedit, just for a laugh) but I get another input/output error. If I try /nvidia1 instead I get a "not a regular file" error, which seems more reasonable.

The last thing I looked at was /proc/driver/nvidia/cards/0 and /1. /0 gives:

> Model:          GeForce 7300 GS
IRQ:            16
Video BIOS:      ??.??.??.??.??
Card Type:      PCI-E
DMA Size:      32 bits
DMA Mask:      0xffffffff
Bus Location:      02.00.0but /1 gives:

> Model:          GeForce 7300 GS
IRQ:            16
Video BIOS:      05.72.22.34.68
Card Type:      PCI-E
DMA Size:      39 bits
DMA Mask:      0x7fffffffff
Bus Location:      07.00.00Both cards came with the computer, so I would have expected these values to all be the same. The differring DMA Size and Mask and ??s for the Video BIOS look like they should be worrying me (I'm not entirely sure what the DMA values mean).

To me, it looks like my 0 card is broken somehow, and the one that I'm actually using is /1. I had issues on Windows when I added my second monitor (I previously used SLI), which I managed to fix by changing the cards round...

So I guess my questions are:

[LIST]
[*]does this look like an actual hardware error, or something wrong with the NVIDIA drivers?
[*]does anyone have any suggestions for getting my second screen up and running?
[/LIST]
Cheers for any replies; I hope I've provided enough info for people to go on here.

---

### Post by devcaka on 2010-08-31
Hi,

I have the exact same error. nvidia1 seems to be faulty (software or Hardware).

At one point, I played with the bios a bit, and it came back to life until I had to restart. And I lost my second GPU.

And I also get:
Video BIOS: 	 ??.??.??.??.??

Did you find a solution to this issue? or did you just changed the card?

Thanks,

Devcaka

---

### Post by Dave158 on 2010-08-31
I had this problem too. I thought maybe it was just me and I went back to an older edition, seems to have fixed it. Maybe it's just a bug?

---

### Post by devcaka on 2010-09-01
Hi again,

Just to warn anyone with the same issue: I bought another nvidia card, and I have the exact same issue. So, it is definitely not a hardware issue. 

@Dave158, earlier edition of Ubuntu? or Nvidia drivers? I would prefer not to downgrade from Ubuntu 10.04

Thanks
Devcaka

---

