---
title: "How do I change CPU speed on EEE pc 901?"
date: 2009-06-23
forum: Hardware
---

### Post by Textureglitch on 2009-06-23
I'm using Jaunty Ubuntu Netbook Remix on an Asus EEE PC 901. It has a 1.6GHz N270 Intel Atom processor.

I can't get Ubuntu to control the CPU frequency scaling function.

In the default Xandros that came with the netbook there are four different settings for the cpu clockspeed that you can switch between on a button. Asus called it 'hybrid engine' for some reason, the settings are: "power saving", "auto", "high performance", "super high performance".

There's a [detailed description of what each one does here]("http://www.liliputing.com/2009/02/asus-super-hybrid-engine-software-has-a-secret-hd-movie-mode.html"), but the names are self-explanatory.

The problem seems to be that the Atom processor does not support the p4_clockmod kernel module that cpufreq and powernow use on other intel CPUs to control the clockspeed. This module works on eee 900 and the other netbooks that use the celeron chip.

I've tried eeepc-acpi-utils and various other eeepc acpi scripts, but they all rely on cpufreq to do the frequency scaling.
I've tried to get p4_clockmod to load into the kernel, but it keeps saying the resource is inaccessible.

If I check /proc/cpuinfo, the two processors (the Atom has hyperthreading) both show 800MHz, and if I stress the system a lot, this will jump to 1.6GHz so there is some frequency control going on somewhere, possibly in the BIOS?
Attaching the netbook to AC power doesn't trigger any kind of performance mode.

The problem is that the upscaling to 1.6GHz happens rarely and only under prolonged load, and watching a movie is apparently not enough of a load to trigger this behavior, so movie playback gets jagged and keeps skipping, especially when using the VGA out.
It also makes heavy apps like Firefox and Openoffice freeze for 2-3 seconds every once in a while before they react to user input.

This is exactly the same behavior I observed in the Xandros OS previously and forcing the CPU speed to maximum solved the problem and made the computer more responsive.
The current behavior seems a lot like the 'conservative' mode of CPUfreq, which had the same problems last I tested it.

I basically need an 'ondemand' mode for the netbook.

---

### Post by FlyingBuzz on 2009-06-23
You can control CPU speed using gnome-panel applet.
And you can install eee-control to change perfomance modes.
I have Eee PC 901 20 Gb and I know what I'm saying ;-)

---

### Post by Textureglitch on 2009-06-25
> **FlyingBuzz said:**
> You can control CPU speed using gnome-panel applet.
And you can install eee-control to change perfomance modes.
I have Eee PC 901 20 Gb and I know what I'm saying ;-)

I've tried that too and it didn't work. I installed the eee-control jaunty version from the website, but after a reboot it says there's an error communicating with the eee-control-daemon. The daemon is running fine, however, and I've googled for several fixes that didn't work. Most of the fixes are outdated from a time eee-control worked differently, and the rest amount to "try to reload the daemon", which doesn't help.
I've also run the eee-control-setup script and that made no difference.

Exactly how did you get eee-control working?
Can you please see if the p4_clockmod is running on your pc901? It should show up if you type 'lsmod | grep p4" in a terminal.

---

