---
title: "Completely disable ATI graphics card in Ubuntu 12.10 (Quantal)"
date: 2012-10-25
forum: Hardware
---

### Post by HungerGalaxy on 2012-10-25
Hi,

I'm fairly new to Ubuntu (<2 months) and love it so far! One question: I have Ubuntu 12.10 Quantal installed on my Samsung Series 7 14" (no dual boot--once I installed Ubuntu I pretty much stopped using Windows altogether :)). Ever since I upgraded from 12.04 to 12.10, within five minutes of booting the fan would come on at full blast but the CPU would hover around 58-65C, even after repasting. When I was repasting I saw that the heat sink in this laptop is connected to the CPU, GPU, and what I think is the graphics card, so I installed lm-sensors. My Radeon HD 6400/7400M graphics card is never below 70C, and sometimes gets up to 80. If it's attached to the same heat sink as my CPU it seems like that could be what's causing the heat. So my question is: how can I completely disable the card and use only integrated graphics? It seems like Ubuntu doesn't really need the discreet graphics card and disabling it would help out my heat problem (and battery life to boot), but would there be any potential negative affects of disabling it altogether? Any help is appreciated!

---

### Post by punitag on 2012-10-25
Here you go :
[http://techxing.tumblr.com/post/18345688911/disable-your-graphics-card-in-ubuntu-to-improve-battery](http://techxing.tumblr.com/post/18345688911/disable-your-graphics-card-in-ubuntu-to-improve-battery)

---

### Post by HungerGalaxy on 2012-10-26
> **punitag said:**
> Here you go :
[http://techxing.tumblr.com/post/18345688911/disable-your-graphics-card-in-ubuntu-to-improve-battery](http://techxing.tumblr.com/post/18345688911/disable-your-graphics-card-in-ubuntu-to-improve-battery)

Thanks! Worked like a dream, my CPU is always >60C now and the fan only kicks in every once in a while :P

---

### Post by nymusicman on 2012-10-28
Unfortunately this doesn't help those with an AMD processor.

---

### Post by dmoos on 2012-10-30
Doesn't work with a Vaio SB with Hybrid Graphics (Intel Graphics Card and AMD/ATI Radeon HD 6400M/7400M Series) either. Laptop overheats (30W)and the fan is permanently running, I tried to deactivate the AMD, without success. The vgaswitcheroo, I tried it in every variation I could find, other methods don't apply to AMD. Terminal says that is off-powered, but I don't perceive any difference in temperature or energy consumption.
Also ried to get the catalyst running. Does not work.

---

### Post by nymusicman on 2012-10-30
Actually I feel kind of dumb. When I posted my last comment I had forgotten to install the fglrx proprietary drivers on my 12.10 install. However, even though this does stop the fan from constantly running it doesn't really significantly increase battery but that is how it's been for all the ubuntu release on my Acer laptop.

---

