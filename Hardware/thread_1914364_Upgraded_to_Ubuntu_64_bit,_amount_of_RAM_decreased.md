---
title: "Upgraded to Ubuntu 64 bit, amount of RAM decreased"
date: 2012-01-24
forum: Hardware
---

### Post by u-noob-tu on 2012-01-24
Yesterday i discovered that my Dell Studio 17's CPU (Intel Core 2 Duo) is capable of running in 64-bit mode. Knowing that 64-bits is better, i decided to upgrade to 11.10 64-bit. No problems arose until i looked at my system info and saw that the amount of available RAM had decreased by 100MB (went from 3.9GB in 32-bit to 3.8GB in 64-bit). Why on earth did that happen and where did that RAM go?

---

### Post by raja.genupula on 2012-01-24
Have you checked your Integrated graphics card meminfo .?
May be that 100 MB will be taken by that . check it once .

---

### Post by u-noob-tu on 2012-01-24
> **raja.genupula said:**
> Have you checked your Integrated graphics card meminfo .?
May be that 100 MB will be taken by that . check it once .
how would i check the graphics memory specifically?

---

### Post by madvinegar on 2012-01-24
If I remember well, the 32bit systems can read 4gb of ram but can only use the 3gb of it.

Only in 64bit systems 4gb of ram can be read and used.

So, propably when you had the 32bit system, maybe was reading 3.9gb but actually could only make use of the 2,9gb of it.

While now with the 64bit system, it may read 3,8gb of ram but could actually make use of all of it.

---

### Post by raja.genupula on 2012-01-24
give me the output of **sudo lshw -class display**

---

### Post by u-noob-tu on 2012-01-24
Here ya go ```
ryan@ryan-Studio-1737:~$ sudo lshw -class display
[sudo] password for ryan: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc400000-fc4fffff

```
i think "display 1" is referring to my external monitor, but i could be wrong. im currently not attached to it.

---

### Post by AgentZ86 on 2012-01-24
> **u-noob-tu said:**
> Yesterday i discovered that my Dell Studio 17's CPU (Intel Core 2 Duo) is capable of running in 64-bit mode. Knowing that 64-bits is better, i decided to upgrade to 11.10 64-bit. No problems arose until i looked at my system info and saw that the amount of available RAM had decreased by 100MB (went from 3.9GB in 32-bit to 3.8GB in 64-bit). Why on earth did that happen and where did that RAM go?

I'm no expert but formatting hard drives seem to do the same thing for 23bit vs 64bit

Perhaps your memory use for the video has been consumed slighty by allocating the 64bit clusters for video ram instead of 32bit clusters for video ram.

Again I'm just guessing but I can only guess your bios has done this when switching to 64bit mode.

---

### Post by raja.genupula on 2012-01-24
> **u-noob-tu said:**
> Here ya go ```
ryan@ryan-Studio-1737:~$ sudo lshw -class display
[sudo] password for ryan: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc400000-fc4fffff

```
i think "display 1" is referring to my external monitor, but i could be wrong. im currently not attached to it.

ok now use this link that how much RAM taken your Integrated Graphics card . 

[http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/](http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/)

may be this will help you to know the matter about your RAM .

---

### Post by u-noob-tu on 2012-01-24
```
ryan@ryan-Studio-1737:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```
I think that solves it. my laptop is using the full 4gb of memory, and is using 256mb of video RAM, whereas before only 128mb was being used (which explains why it went from 3.9gb to 3.8gb). Now that i have more video RAM, will that translate to better graphics performance (not that integrated graphics can get much better)?

---

### Post by raja.genupula on 2012-01-24
yup! so i think you got what exactly the information regarding your RAM .

---

### Post by AgentZ86 on 2012-01-24
> **u-noob-tu said:**
> ```
ryan@ryan-Studio-1737:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```
I think that solves it. my laptop is using the full 4gb of memory, and is using 256mb of video RAM, whereas before only 128mb was being used (which explains why it went from 3.9gb to 3.8gb). Now that i have more video RAM, will that translate to better graphics performance (not that integrated graphics can get much better)?


Well, better performance on the card only maybe.

I would say it would give perhaps better performance on the computer overall, but I don't thing this will really effect the video performance a whole lot

The problem with video performance is there is many details to this topic and adding memory to a low performance card likely will have no effect.

I figured this out myself on a low end card and performance can be measured in things like

transfer rate
memory bandwidth and bits such as 128bit or more some cards only have 64bit which is not very good.
shader processor and processor clock multiplier
pixels per clock

However for movie video more memory for video is better but for games  no so much.

It's a bit hard to describe the various effect that one may notice with games on a lower end card and yet depending on the activity and the actual game you may notice no effects from a low end video cards and be just fine.

However it is more critical on some games and activities to at least have faster transfer rates on the upside of 28GB/s
And pixels per clock should be at least 96

And 128bit card or better is best for games

Here is a list of specs to compare:

[http://www.hardwaresecrets.com/article/NVIDIA-Chips-Comparison-Table/132]("http://www.hardwaresecrets.com/article/NVIDIA-Chips-Comparison-Table/132")

---

