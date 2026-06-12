---
title: "Dell Inspiron 5160: heating cycle"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by slightly72 on 2006-04-24
Hi,

I have a Dell Inspiron 5160, w/ Pentium 4, 2.8 GHz, running Breezy. My problem is this: even when I'm not doing anything, the CPU temperature is cycling between 51C and 56C. The temperature rises constantly, up until it reaches 56C, then the fan kicks in, the temperature drops to about 51C (fan's turned off at 52), and then it starts to rise again. The cycle is about 1minute fan on, 1 minute fan off. It's quite annoying. 

Some more background on this machine. It used to run constantly at 72-78C. Did a lot of cleaning (taking it apart and cleaning the fan and puting new thermal paste), disabled a lot of stuff (apmd among other things), took off the battery for better ventilation. I've also disabled frequency scaling from BIOS (w/ frequency scaling the temperatures were 6-7 degrees higher, and the fan constantly on), but kept hyperthreading on. All these got the temperature down to what it is now (51-56). I've played with gkrellm/i8k plugin, but that just modifies the interval when the fan is on, and not the overall behavior.

Running top does not show me anything eating clock cycles, pretty much everything is at 0, except for top (0.3).

So, I'm mystified what could cause the processor to do work to heat itself up. I realize that this might be a shot in the dark, since Dell Inspiron 51xx laptops are known to have poorly design cooling systems and to overheat (wish I had researched that before buying it) -- but is there anyone out there that has/had a similar machine and fixed this issue.

It seems to me that the only solution now would be to buy one of those laptop coolers, but I'm afraid that adding two extra fans would not reduce the noise problem. Anyone used laptop coolers? Are they noisy?

---

### Post by dangermouse28 on 2006-04-28
Dunno if this helps - I have an HP ZD7000 which, like your machine has a P4 processor and tends, by design, to run very hot. I installed Dapper Beta and installed the temperature monitor. It showed cpu temperature to be circa 40 Degrees at idle and 48-50 Degrees when loaded up. The battery also lasted less than an hour. 

I added p4-clockmod to /etc/modules and rebooted

I then added the frequency scaling applet to the panel.

The displayed CPU freq dropped in stages from 3GHz to 2.25GHz. Over 10 mins, the displayed temperature also dropped from 42 Degrees to 34.

I find now that starting from cold, the machine will idle at 30-32 Degrees, 2.25GHz and the battery lasts for just over 2 hrs.:-D 

It is possible to get the cpu to run at lower frequencies but I can't be bothered re-compiling a vanilla kernel and fixing everyhting which breaks in the process!

---

### Post by slightly72 on 2006-04-28
Thanks for the tip with p4-clockmod, somehow, even if I knew about it, overlooked it when looking at 686-smp kernel modules, and thought it comes only for the 386 kernel, to give some P4 functionality. By adding this module, and enabling the speed-step technology from BIOS, now powernowd manages to correctly detect that the processor has 8 speed-steps (349MHz--2.8GHz) -- before, there were only two steps (1.8 and 2.8GHz). I was disabling the speed-step technology since the processor was hotter (about 6-7 degrees) with it than without it.

However, the temperature now hoovers around 58C, and the fan is constantly on (lowest speed). If I do pretty much anything (say, open Firefox, compile some short programs), the temperature immediately jumps over 60, and the second speed of the fan kicks in, which lowers it to about 56, and then the cycle repeats.

One more question though. The processor has hyper-threading, which is enabled in BIOS, and recognized by the 686-smp kernel (i.e. I "have" 2 cpu's). The frequency applet indicates 349MHz for CPU0 and 2.8GHz for CPU1. Not sure what to understand of this, as far as I know, the two would work with the same clock signal (is this true?). How can I make powernowd to lower the frequency for CPU1 too, if indeed it can be done and it's not some fluke reading?

---

### Post by slightly72 on 2006-04-29
One more follow-up.

I've played with various settings for the computer (w/ and w/o speed step, w/ and w/o hyperthreading, w/ and w/o p4-clockmod). Basically, the behavior is pretty much the same: when doing nothing, the cpu just keeps heating up, then the fan kicks in, temperature drops, and the cycle repeats. It's just that the end temperatures vary: with speed step, p4-clockmod, ht, it's between 55 and 59C, w/o speed step it's 51 to 56C. Without speed step, the processor has a max frequency of 1.8GHz, and 4 steps (each 25% apart), fan alternating between off and low speed; with speed step, max 2.8GHz, 8 steps, each 12.5% apart -- but the fan is constantly on, alternating between low and medium speed. Without p4-clockmod, the frequency applet reports either a flat 1.8GHz (w/o speed step), or alternating between 1.8 and 2.8 (w/ speed step) -- but that's probably unreliable. Hyperthreading on or off does not seem to have an influence on the temperature.

It seems that there's not much I can do, the laptop heating system being designed as it is.

---

### Post by dangermouse28 on 2006-05-03
I seem to remember reading somewhere that there were issues with the frequency applet on some machines - not dealing with HT processors properly. Mine's ok but that's not much help to you.

The only other suggestion I have is to take your laptop apart (again!) and see if there's any room to attach RAM heatsinks to the heat transfer / cooling kit. I've seen this method done on my model of HP laptop with some success - it just increases the passive thermal transfer capacity of the cooling system by adding additional fins.

Otherwise, you may have achieved the best possible for your machine.:neutral:

---

