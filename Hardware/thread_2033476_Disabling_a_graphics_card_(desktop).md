---
title: "Disabling a graphics card (desktop)"
date: 2012-07-26
forum: Hardware
---

### Post by L R C on 2012-07-26
I've got a desktop running Ubuntu 11.10 with an XFX 6850 and I tend to leave my computer on overnight if I'm downloading stuff. Since my computer's in my bedroom this creates some problems for me: the XFX card's fan has been described in various reviews as "deafening", "like a fighter jet taking off" and "a bit louder than I'd like". I looked into replacement fans but it seems that there isn't a 6850 on the market that uses the reference design, and since XFX are one of the less popular vendors (compared to something like Sapphire) this means there aren't any replacement coolers for my card.

Which brings me on to my question: is there any way to completely disable my graphics card (ie cut the power supply to it so it doesn't do anything, meaning it doesn't produce heat so the fan isn't needed) while the computer is on? Ideally some sort of command, then when I want to reenable the card I can simply type another command in (and hope I don't make any typos...). Has anyone heard of this being done? My motherboard doesn't have integrated graphics so I can't use those instead.

I suppose I could just spend 50p on a set of earplugs, that's a slightly less fun solution though.

---

### Post by TheFu on 2012-07-26
If the GPU isn't driving the monitor, does that make it quieter?  If you look at the power settings, there is a monitor sleep timeout.  [https://wiki.ubuntu.com/power-management-in-Ubuntu](https://wiki.ubuntu.com/power-management-in-Ubuntu) seems related.

---

### Post by L R C on 2012-07-26
Not considerably... I lock the screen a lot of the time which stops any video output, hence I don't really see why the GPU has to be on at all when the screen's locked. Perhaps there's some way to integrate turning off the GPU with locking the screen?

---

### Post by TheFu on 2012-07-26
> **L R C said:**
> Not considerably... I lock the screen a lot of the time which stops any video output, hence I don't really see why the GPU has to be on at all when the screen's locked. Perhaps there's some way to integrate turning off the GPU with locking the screen?

It would be a feature of the GPU and the motherboard (if it was even possible). I would expect only hot-swap cards to support turning power off completely to an addon card. Without much demand to support these cards, I'd expect that Linux doesn't. If it were supported, it would come from the GPU vendor in their driver.

Sorry, I'm not big on graphics cards that have fans. I always buy GPUs without any fans and have good cooling in the case to prevent heat issues.

[http://www.tomshardware.com/news/nvidia-gpu-optimus,9788.html](http://www.tomshardware.com/news/nvidia-gpu-optimus,9788.html) seems related. Interesting.

---

### Post by L R C on 2012-07-26
> **TheFu said:**
> Sorry, I'm not big on graphics cards that have fans. I always buy GPUs without any fans and have good cooling in the case to prevent heat issues.

[http://www.tomshardware.com/news/nvidia-gpu-optimus,9788.html](http://www.tomshardware.com/news/nvidia-gpu-optimus,9788.html) seems related. Interesting.
I wasn't aware those existed! Anyway, thanks for your help, the link is indeed interesting. I was thinking, the card is powered by two 6-pin connectors straight from the PSU. Do you think it would be safe to make a physical switch to interrupt the power supply to the card? Or would that leave me with a still-hot card and no fan to cool it down?

---

### Post by QIII on 2012-07-26
I think it would be inadvisable to unplug the cables.  Your card also draws some of its power through the PCIe slot.  I don't think you could predict what would happen.  You might damage the card or the mobo or both.

---

### Post by L R C on 2012-07-26
Okay :( well thanks for your help anyway TheFu and QIII!

---

### Post by QIII on 2012-07-26
Sigh...

I resisted this because it is extremely dangerous, but do some googling on ```
aticonfig --pplib-cmd "set fanspeed 0 70"
```where 0 is the adapter number (zero-based index, so 0, 1, 2 ...) and 70 can be replaced with the percent of max fan speed you want.

Again, this is **dangerous**.  I won't recommend the approach, but I'll throw it out there for you.  If you set the fan speed too low, you can smoke your card.  And you would have to remember to set it again later to a higher percentage.  It's better to let the card use its own built in controls, since it is designed that way.  You would need to weigh that very carefully.

Resetting the fanspeed to "auto" sometimes does not work.

---

### Post by L R C on 2012-07-26
> **QIII said:**
> Sigh...

I resisted this because it is extremely dangerous, but do some googling on ```
aticonfig --pplib-cmd "set fanspeed 0 70"
```where 0 is the adapter number (zero-based index, so 0, 1, 2 ...) and 70 can be replaced with the percent of max fan speed you want.

Again, this is **dangerous**.  I won't recommend the approach, but I'll throw it out there for you.  If you set the fan speed too low, you can smoke your card.  And you would have to remember to set it again later to a higher percentage.  It's better to let the card use its own built in controls, since it is designed that way.  You would need to weigh that very carefully.

Resetting the fanspeed to "auto" sometimes does not work.

I definitely wouldn't do this, the AMD Catalyst thing on Windows (I use it every few days) doesn't let me set it below 20% so I'm guessing the card generates more heat when idling than 20% fan speed can get rid of.

I could have a go with this (maybe in a live cd) without using a desktop environment so the card doesn't do much work, and check the temperature every few minutes with lm-sensors... although I haven't been able to get that working with my graphics card...

I'd rather spend a bit on a pair of earplugs than buy another 6850, so it's probably best if I leave it alone for now.

---

### Post by QIII on 2012-07-26
lm-sensors doesn't detect the ATI GPU temp, fan speed, load, etc.

For my conky, I have it call an .sh that parses the results of

```
aticonfig --adapter=all --od-gettemperature
```

Overdrive does not have a graphical interface in Linux.  It's command line only.

---

