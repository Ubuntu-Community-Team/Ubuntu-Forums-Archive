---
title: "Nvidia GTX 460M is being underclocked"
date: 2011-06-25
forum: Hardware
---

### Post by Scott O'Nanski on 2011-06-25
Greetings,

My laptop (Alienware M15x) video card (Nvidia GTX 260M) is being under-clocked to 275 Mhz (Graphics Clock), 301 MHz (Memory Clock) and 550MHz (Processor Clock)when using the Nvidia control panel PowerMizer

The normal clock speeds are 550 MHz (Graphics Clock), 950 MHz (Memory Clock) and 1350 MHz (Processor Clock).

I've been trying to find a solution to fixing this but haven't come up with any solid resolution.

If anyone can provide me with additional information about this, or on how to fix it, I would be greatly appreciative.

Thanks,

Scott.

---

### Post by Yellow Pasque on 2011-06-25
If you're checking the speeds when idle or low load, then they're going to be underclocked to save power..

---

### Post by Scott O'Nanski on 2011-06-25
> **Temüjin said:**
> If you're checking the speeds when idle or low load, then they're going to be underclocked to save power..

Is there anything I can edit to force the card to run at full speeds at all times?

---

### Post by Yellow Pasque on 2011-06-25
[http://guilleml.wordpress.com/2011/04/27/nvidia-powermizer-on-linux/](http://guilleml.wordpress.com/2011/04/27/nvidia-powermizer-on-linux/)

---

### Post by Scott O'Nanski on 2011-06-27
> **Temüjin said:**
> [http://guilleml.wordpress.com/2011/04/27/nvidia-powermizer-on-linux/](http://guilleml.wordpress.com/2011/04/27/nvidia-powermizer-on-linux/)

Thanks for posting that. However, I don't understand what I should edit to enable full performance. The author, and subsequent articles do not go into specific detail.

---

### Post by Scott O'Nanski on 2011-06-28
Found a command. Here it is;

sudo nvidia-settings -a [gpu:0]/GPUPowerMizerMode=1

---

### Post by wh20250 on 2011-10-04
Were you able to get the full clock speed out of your gtx260m. The best I can get is Performance level 1 Graphics 275 Memory clock 301. And that is under load (ie. running Rift in wine). I keep searching but can't seem to find much info. Everything that is listed simple changes PowerMizer from adaptive to max performance, but it seems to think max performance is Performance Level 1. While Nvidia X Server lists 2 more levels (2 and 3) with 3 showing the proper specs for the 260m. If anyone can shed any light on how to get this card to live up to its potential it would be greatly appreciated.

Alan
Alienware m15x
Intel(R) Core(TM) i7 CPU Q 840  @ 1.87GHz
Nvidia gtx 260m
128 GB SSD 8 GB 1333 DDR3

---

