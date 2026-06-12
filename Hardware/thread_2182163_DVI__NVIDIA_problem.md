---
title: "DVI / NVIDIA problem"
date: 2013-10-20
forum: Hardware
---

### Post by geloki on 2013-10-20
Hi,

I'm troubleshooting a DVI/NVIDIA problem and I'm a bit lost. I hope you can help. I changed my monitor setup and am now experiencing fliquering in parts of the screen.

The old setup that worked: DVI -> VGA adapter on DVI-I-1 port of my graphics card. VGA cable to a monitor with resultion 1280 x 1024.

The new setup that has the fliquering: DVI cable on DVI-I-1 port to an other monitor with resolution 1920 X 1080.

If I connect the new monitor using VGA, the old cable and the DVI -> VGA adapter then there is no problem.

At first this sounds as if either the DVI cable or the new monitor's DVI port is at fault but there is more. The details of the "fliquering" rather suggest a driver/graphic card problem. Some symptoms:

When booting all parts that grub draws in black when using VGA fliquer using various colors. (There is some pattern visible.) The parts that are drawn in a different color are fine. Once Ubuntu has started things are mostly fine except, if the youtube flash player is running. As long as video does not have started the video screen should be black. This is not the case. The same thing as during the boot happens. Once the video plays the image is mostly fine. However, there is some fliquering going on on the desktop image. (This time without any apparent pattern.) The strange part is that if I change tabs in firefox moving the youtube video to the background then the fliquering changes in intensity. 

I also tried booting Windows. It has similar problems during boot. I have not yet tried flash under Windows.

This is very strange:
* I do not think that the cable or the monitor are at fault because the symtoms vary depending on the position of the flash window.
* I do not think that the NVIDA drivers are at fault because the problem already occurs at the bootloader stage, i.e. the drivers have not already been loaded.
* My graphics card gets VGA correct on the same port, so I do not suspect it.

Maybe a BIOS bug?

I really have no clue, as to what the problem is. Please help. :(

---

