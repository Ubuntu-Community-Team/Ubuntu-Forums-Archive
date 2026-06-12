---
title: "DELL XPS15 (L502X) heating and fan noise"
date: 2016-07-29
forum: Hardware
---

### Post by senor_massao on 2016-07-29
Hi,
My laptop was heating up a bit too much (temperature above 90’s in normal load, and sometimes shutting down after hitting 100C), so I finally decided to open up my Dell XPS 15 (L502X) and replace the thermal paste. I have few questions:
When I opened it up, apart from the thermal paste on the cpu (i7-2630QM) and gpu (Nvidia GT-540 2gb), there were several white pads, and one grey pad. The grey pad was above the motherboard HM67 chip. This is the first time I ever saw a heat sink with thermal pad needed to cool down the motherboard. Or am I missing something? And what are all these small white pads? They seem to be covering different chips on the motherboard. Does anyone know the width of these white pads, and grey pads? Are all of these thermal pads to conduct heat? Or some are meant to block heat? I think the white ones are meant to block heat, but I may be wrong.
Anyhow, after replacing the thermal paste (didn’t do anything with the pads, since I wasn’t expecting to see them anyway), the temperature of CPU and motherboard remains in 70’s C, and GPU in 60’s C under normal load (20 browser tabs, and some MS Office work alongside). But the fan works in an annoying manner with bursts of sounds, instead of constant sound. It is rather annoying, and I rather have the fan working the whole time than these annoying bursts (fan on, fan off, fan on, fan off, and goes on like this constantly). Any solution to fix this?
I am also considering downgrading to I5-2540M (lower TDP, and dual core), but its not worth it if the fan is going to behave in similar manner.

---

### Post by weatherman2 on 2016-07-29
Silly question: when you replaced the thermal paste, did you make sure you cleaned all the dust and dirt from the vents, too?  Was there dirt and dust in there when you removed the heat sink and from around the fan?  (With a laptop that old, I'd expect some dirt/dust, which is usually the biggest contributor to overheating.)

The heat sink is designed to draw heat off of all of the components it is touching.  Those "pads" are the equivalent of thermal paste.  But not all the chips get equally hot.  Could be the pads will have melted on some chips (like the CPU) but not on others.  You could scrape the pads off if you wish and just apply new thermal paste, but I'm not sure if it would matter.  Depends on the condition of the pads.

Some laptops are better designed than others in terms of getting hot.  Having a separate GPU definitely adds heat.  Could be this model Dell - XPS is designed for performance - simply runs hot and will always run pretty hot, even if you get a slightly cooler CPU.  70C sounds hot to me, but that may be normal on that laptop with the fan coming on like that.  (Do a web search for a utility that may add manual fan control; the BIOS may also have an option to have the fan run at 100% all the time, something I'd personally find annoying, though.)

It may not be possible on that particular Dell, but I might be more inclined to replace that Nvidia GPU or just remove it to use the built-in graphics on the i7.  (That's a Sandy Bridge / 2nd generation i7 and it has integrated graphics on the CPU.)  In some laptops, the separate GPU may be an option; you may be able to get a cooler graphics card that uses the integrated graphics on the i7.  Could be the XPS didn't have that option as it's designed for performance.

You might even try an Ivy Bridge (3rd gen) CPU instead of going to a slower 2nd gen Sandy Bridge.  The TDP should be cooler on an Ivy Bridge, and it's the same socket.  But would an ivy bridge work in your Dell?  Depends on the design and whether the BIOS would support it.  I wouldn't be surprised.  I've done similar upgrades on older Dell laptops before.

Having said all of that...you might try Dell's support forums with this same question, as your question isn't specific to Ubuntu.

---

