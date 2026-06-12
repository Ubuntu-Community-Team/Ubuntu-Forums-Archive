---
title: "GAHHHH i dont get a bios!"
date: 2009-12-27
forum: Hardware
---

### Post by FreezWay on 2009-12-27
I just swapped mobos and lo and behold I power up.... the lights turn on (oops got the power and disk activity leds mixed up) fans whir, screen goes black, i wait, screen stays black, I press the power button (miswired), I press the power button on the psu. It shuts off.
I now have the power and reset buttons wired correctly, but I still get null on my moniter. Not even a bios! any help appriaciated.
Until then I am resticted to an old P4 with 512MB ram and GeForce FX 5200. Please help.

---

### Post by lidex on 2009-12-27
You tried removing the battery or using the jumper to reset bios?

---

### Post by diablo75 on 2009-12-27
Pull all but one stick of RAM, and then turn it on.  Be sure the PSU is unplugged while swapping RAM sticks, then plug it back in when you're ready to test.  The reason for this is that sometimes motherboards continue to pump a little power through the board, even if it's "off", and this could result in an accidental short on your stick while swapping.  

You might have one bad stick of RAM, or the mobo requires certain sticks to be placed in certain slots.  If you know one stick works, pull it, and replace it with the other on.  If you confirm that both sticks work by themselves, then it's an issue with what slots they fit in.  This has something to do with "bank interleaving".

---

### Post by FreezWay on 2009-12-27
hmmm its doesn't seem to have a bios jumper (my friend gave me the board.) The RAM is brand new, b/c i needed DDR2 for this mobo and i only had ddr3. I can try removing the battery or do i need a bios jumper first. I'll try it without one of the sticks of RAM.

---

### Post by lykwydchykyn on 2009-12-27
Try disconnecting ALL the hardware except RAM: Video card, drives, cards, etc.  If you have IDE drives this can happen when the jumpers are misconfigured, and it can happen if the video card is taking too much power.

If it POSTS like this, then try adding back one piece of HW at a time to see when it starts failing.

---

### Post by FreezWay on 2009-12-27
Taking one one stick of ram didn't help. The only things plugged in are my HDD, optical drive, ram and CPU. Will it boot without a bios jumper?

---

### Post by llawwehttam on 2009-12-27
remove the battery and short circuit the terminals underneath t with a screwdriver. That will clear CMOS and should solve the problem. If not unplug everything from the back and hold the power button in for 30 s the plug everything back in and try again.

---

### Post by viper250 on 2009-12-27
your bios jumper usually needs to be in place because that is a bridge for the bios battery
if the jumper is removed it clears the cmos of its setting and you have to re input the settings. Some boards had a clear cmos setting and some boards had a cmos block setting that protected the cmos file from being written to. This setting was developed when they came out with the cmos boot viruses ( some people lost the mobos because of them)

---

### Post by FreezWay on 2009-12-28
i fixed it, turns out the cpu didn't like the mobo

---

