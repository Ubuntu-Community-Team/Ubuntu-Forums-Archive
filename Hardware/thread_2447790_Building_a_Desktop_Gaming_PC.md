---
title: "Building a Desktop Gaming PC"
date: 2020-07-26
forum: Hardware
---

### Post by MaximB on 2020-07-26
Hello,
So it's about time for me to build a desktop gaming PC that will hopefully last for years to come...
I was wondering in terms of hardware compatibility and drivers, what is best for Ubuntu?
Is there a preferred vendor for CPU? Intel i9 or AMD Ryzen 9 3900?
In graphic cards I understand Nvidia (2070) is still the way to go...
Also there are many Nvidia 2070 models, how do I know which to choose?
And what is a good motherboard for Ubuntu?

Thank You,
Maxim.

---

### Post by CatKiller on 2020-07-26
> **MaximB said:**
> Is there a preferred vendor for CPU? Intel i9 or AMD Ryzen 9 3900? 

In terms of compatibility: no. In terms of performance: AMD has the edge in most workloads. You can find benchmarks for the particular applications you're interested in. 

>  In graphic cards I understand Nvidia (2070) is still the way to go... 

I haven't followed it closely (I've had a 2080 Ti since launch, so I won't need one myself for a while) but I understand that the Super versions improved the price-to-performance enough that one would favour a Super over a non-Super. 

Nvidia's drivers being proprietary means that there is an initial setup step that you wouldn't have to do with AMD cards, and they don't cooperate as well with the wider Linux ecosystem. That will be more of an issue for some users than others. Also AMD benefits more from the newest software (kernel and graphics stack), because it's all built in, than Nvidia with their external proprietary stack. 

Phoronix do gaming benchmarks on Linux so that you can see which ones meet your needs. Relative performance isn't necessarily the same under Linux as it would be under Windows. 

>  Also there are many Nvidia 2070 models, how do I know which to choose?  

The 2070 and the 2070 Super are different tiers. Within each tier the cards are essentially the same, differing by default (over)clocks, size, and fan design. If you have an enormous case and you don't care about noise you can just put whatever you have available in there. If you're bothered by noise there are reviews that will compare the fan noise from different models. If you're using a small case, or want to use other cards at the same time, then you'll need to pay more attention to sizing. 

>  And what is a good motherboard for Ubuntu?

Motherboards themselves are rarely an issue, it's the onboard stuff that's potentially problematic.

For WiFi Intel should be strongly favoured; for ethernet Intel should be mildly favoured. Non-Intel WiFi is pretty terrible, but non-Intel ethernet is mostly OK.

For sound, the "value added" stuff is what will cause potential issues. Perfectly standard sound devices doing perfectly standard things are generally well supported. You can search for "<chip name> linux" to see if other people have had any issues.

Sensor readings on some motherboards (for checking temperatures or controlling fans) might not be easily available, but it's hard to tell that in advance. Processors can report their own temperatures, so you should have access to that whichever other sensor chips are on the motherboard.

RGB lighting won't be natively supported. There are projects to try to reverse-engineer them, but they are a work in progress. Safest to assume that they'll be set to a default flashing rainbow and be difficult to turn off.

Premium business motherboards have been my sweet spot: high quality components with no shenanigans or bling.

---

### Post by pqwoerituytrueiwoq on 2020-07-26
If you are looking for the best gaming specific CPU today that would be the i5-10600k with a OC and fast ram, you would need a Z490 board and the decent ones start at $200, so the CPU and board will cost around $500
If you care about price/performance and being good enough look at a R5 3600 ($160 at newegg today) and a B450/X470/B550/X570 chipset motherboard (be sure to not get ram slower than 3200), i do suggest checking this [spreadsheet]("https://docs.google.com/spreadsheets/d/1d9_E3h8bLp-TXr-0zTJFqqVxdCR9daIVNyMatydkpFA/edit#gid=611478281") to be sure the VRM on the board is not crap, this is mainly for the sake of having the option to higher end CPU later
outside of gaming amd's current offerings wreck what intel has to offer in a given price bracket as opposed to a marginal lose, at the end of the day it is about the right tool for the job at hand, AMDs upcoming chips are rumored to be significantly better, so it may be a better to go with amd even if you have a reason get a 10600k, the next few years are gonna be rough for intel's cpu division, but there managers and CEOs need to learn a lesson that will be vital to the survival of there cpu division

some motherboards have a switch to turn RGB off and for the most part you can go this on a GPU by unplugging the leds, if you want control over it look at [openrgb]("https://gitlab.com/CalcProgrammer1/OpenRGB") and [msi-rgb]("https://github.com/nagisa/msi-rgb")
personally i use msi-rgb, but all i want to do it turn the LEDs off [FONT=courier new]msi-rgb -x 0 0 0[/FONT]

---

