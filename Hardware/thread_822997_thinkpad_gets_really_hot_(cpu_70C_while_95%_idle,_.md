---
title: "thinkpad gets really hot (cpu 70C while 95% idle, w/ clean heatsink)"
date: 2008-06-08
forum: Hardware
---

### Post by schlesinger on 2008-06-08
Hard drive about 45C average (using smartctl), so no big deal, but both cores run to about 70C (using acpi -V). Top shows that CPU is 95% idle. Occurs about an hour after turning the computer on, every time. It's Thinkpad x60, core 2 duo, and I believe I've heard reports of this happening... The heating doesn't seem to happen with Windows Vista, so it's not a badly cleaned heatsink or fan--I think it's just a bad hardware configuration or something? It's annoying, because not only does the handrest get very hot, but the fan also turns on and is very loud. 

What could be causing the heat? Thanks lots..

---

### Post by ryansinn on 2008-08-07
> **schlesinger said:**
> Hard drive about 45C average (using smartctl), so no big deal, but both cores run to about 70C (using acpi -V). Top shows that CPU is 95% idle. Occurs about an hour after turning the computer on, every time. It's Thinkpad x60, core 2 duo, and I believe I've heard reports of this happening... The heating doesn't seem to happen with Windows Vista, so it's not a badly cleaned heatsink or fan--I think it's just a bad hardware configuration or something? It's annoying, because not only does the handrest get very hot, but the fan also turns on and is very loud. 

What could be causing the heat? Thanks lots..

I'm seeing this too -- I got to pickup my laptop off my desk first thing in the morning (after it's been idling all night) and it's too hot for my lap... something is going on here -- You're also right... Vista isn't like this.

I'm running Hardy 8.04 installed from scratch at the release of 8.04 FINAL.

---

### Post by SadaraX on 2009-01-30
I'm using a Thinkpad t61 and I am seeing similar things. My machine never used to ***constantly*** spin the fans on and off, but now it does within 15 minutes of booting. It does not matter whether the machine is 100% idle or whether it is doing 100% work.

My temperatures are kept around 38C by the fans, but the speed is noticeable.

The fans never seem to spin at 10% or 50% speed, but ***always*** at 100% speed. This might be a contributing factor.

I opened my case last week and checked all the components for dust. There was basically no dust in the fans and intake ports. I blew them out anyway and the performance is the same.

This did not happen when using Ubuntu 7.10. I only recently switched to Hardy 8.04.2 and the difference was immediate and apparent.

---

### Post by ryansinn on 2009-02-01
I fixed my issue by moving to an ssd drive.

System runs about at room temp,but much faster than before.

---

