---
title: "Cannot use iGPU and stuck in software rendering"
date: 2019-12-12
forum: Hardware
---

### Post by plb2010 on 2019-12-12
I recently built a new system using an ASrock Rack E3C246D4U motherboard and a Xeon E-2288g. The box has no GPU installed and my intention is to use the iGPU that comes with the CPU. I installed Ubuntu 19.10 (desktop version) via the IPMI and rebooted only to have the system freezes at a purple screen. Couple more reboots and the same result… When it is in this state, the directly connected keyboard and mouse are unresponsive as are the virtual ones via the IPMI interface—well, sometimes the mouse will wiggle around but the keyboard might as well be unplugged.  The only way that I have been able to get it to fully boot and bring up Gnome is to add nomodeset via the GRUB edit feature when booting and then permanently add it to the grub file once the system is up. (I also removed the quiet-splash flag from the grub file so that I could better see what was going on during boot.)  Now it boots but I am stuck with a 640x480, 8-bt color, slow as dirt UI because the iGPU is being bypassed in favor of software rendering. Does anyone have ideas on how I can regain the use of the iGPU and avoid the freezing of the system?


Other things to note. Once I was able to get it up and running, I did do a sudo apt update/ apt upgrade AND set the default graphics in the BIOS to use the iGPU.


Also (I am a bit new to Linux) where can I find information on what gets disabled when nomodeset is applied and or find system logs of possible errors/conflicts occurring at boot?

Many thanks in advance for any and all ideas and support offered!

---

### Post by Yellow Pasque on 2019-12-14
First off, make sure latest BIOS is installed as that adds official support for the Xeon E-2200 series.

> The box has no GPU installed and my intention is to use the iGPU that comes with the CPU

I don't think that's possible. The board's VGA port is connected to the ASpeed AST2500, which only provides a very basic 2D GPU. If you wanted to use the iGP on the CPU, the board you wanted was the ASRock Rack C246M WS.

---

### Post by plb2010 on 2019-12-15
> **Yellow Pasque said:**
> First off, make sure latest BIOS is installed as that adds official support for the Xeon E-2200 series.


I don't think that's possible. The board's VGA port is connected to the ASpeed AST2500, which only provides a very basic 2D GPU. If you wanted to use the iGP on the CPU, the board you wanted was the ASRock Rack C246M WS.

Yes. The bios are the latest.

This is true. Sorry, what I was trying to convey was that I don't have a graphics card (Nvidia or AMD) plugged into the board. And yes, I did eventually figure out through googling and poking around at the command line that the UHD630 graphics on the CPU is simply not supported by this board. I stuck a secondhand GTX 1050 in it and my problem is solved.

Thanks!

---

### Post by Yellow Pasque on 2019-12-15
> **plb2010 said:**
> Yes. The bios are the latest.

This is true. Sorry, what I was trying to convey was that I don't have a graphics card (Nvidia or AMD) plugged into the board. And yes, I did eventually figure out through googling and poking around at the command line that the UHD630 graphics on the CPU is simply not supported by this board. 

I stuck a secondhand GTX 1050 in it and my problem is solved.Thanks!

Mmhmmm. Please mark the thread as solved.

---

