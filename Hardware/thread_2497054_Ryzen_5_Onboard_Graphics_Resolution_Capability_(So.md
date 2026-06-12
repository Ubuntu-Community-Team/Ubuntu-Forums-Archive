---
title: "Ryzen 5 Onboard Graphics Resolution Capability? (Solved)"
date: 2024-04-21
forum: Hardware
---

### Post by wmichaelb2 on 2024-04-21
Hi, I recently rebuilt an older machine with an ASUS Prime B450M-A II  AMD AM4 motherboard, 64G of RAM, 1 TB NVME M.2 drive, and a Ryzen 5  5600GT processor. I'm not a gamer; I'm running Ubuntu Studio 22.04,  using the onboard graphics. My primary uses involve music editing, and  I'm running a 28" LG monitor that maxes out at 1920 x 1080. 

My question is, does the onboard graphics for this motherboard max out  at this resolution with Ubuntu? I really could use enough resolution to display two or more windows at once. If I got a monitor with higher  resolution, would the onboard graphics support it, or will I also need a  graphics card? Any feedback is welcome, and thanks in advance.

---

### Post by him610 on 2024-04-21
@wmichelb2
Don't know if this will help or not.
Here is what the specs say about your MB graphics ....
> Integrated Graphics in the 2nd and 1st Gen AMD Ryzen™ with Radeon™ Vega Graphics/ Athlon™ with Radeon™ Vega Graphics Processors *
1  x D-Sub
1  x DVI-D
1  x HDMI 2.0b
*Graphics specifications may vary between CPU types.
Here is what AMD says about Ryzen 5600GT graphics...
> Graphics Capabilities
Graphics Model
Radeon™ Graphics
Graphics Core Count 7
Graphics Frequency 1900 MHz

I use a B450M with Ryzen 5600G with (general purpose) monitor, Acer R240HY res: 1920x1080
When I go into Settings > Display, max setting is 1920 x 1080.
I had mine connected to 29 inch monitor a few months ago, and I think one could use a higher resolution.

Here is what a search turned up
> The AMD Ryzen 5 5600GT is a desktop processor that features Radeon graphics cores so you can play games in 1080p without a dedicated graphics card. It has 6 cores and 12 threads, operating frequencies of up to 4.6 GHz, and 16 MB of L3 cache. The graphics cores are based on the Vega architecture and are clocked at a frequency of 1.9 GHz. The graphics cores share the system's main memory as graphics memory. 


---

### Post by Yellow Pasque on 2024-04-22
The 5600G/T is fully supported by Linux. Whatever the hardware is capable of will work. So HDMI 2.0b means 3840&#8201;×&#8201;2160 @ 60Hz will work with appropriate cable.

---

### Post by wmichaelb2 on 2024-04-25
Thanks, Yellow Pasque! That's what I needed to know.

---

