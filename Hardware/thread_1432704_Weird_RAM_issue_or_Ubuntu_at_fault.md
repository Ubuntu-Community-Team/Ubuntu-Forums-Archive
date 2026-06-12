---
title: "Weird RAM issue or Ubuntu at fault ?"
date: 2010-03-18
forum: Hardware
---

### Post by mohitchawla on 2010-03-18
Hello folks, I faced a strange problem last night.

I just set the timings, frequency & voltage of my RAM as per the company-recommended settings at 1333MHz(using memory ratio equal to 5 on my motherboard), 9-9-9-24 @ 1.5V for the particular model (in sig).

The thing is I tested the settings in memtest86+ for over an hour without errors (one complete pass).

However, when I booted into the OS, and started doing some web browsing, the system rebooted. This happened twice.

I am still using the same settings, and nothing has happened yet.

My questions:

1. Could this possibly be a software issue ?
2. What could have led to the reboots ?
3. I have been running the system now for over two hours now, and nothing has happened yet. Should I be worried still ?

---

### Post by cascade9 on 2010-03-18
It could be your RAM speed settings, but its probably more liekly that you got a minor power blimp. 

BTW, the 1333 setting is overclocked- 

[http://www.msi.com/index.php?func=prodmbspec&maincat_no=1&cat2_no=&cat3_no=&prod_no=1804](http://www.msi.com/index.php?func=prodmbspec&maincat_no=1&cat2_no=&cat3_no=&prod_no=1804)

---

### Post by norseman-has-a-laptop on 2010-03-18
in my opinion i think its your ram but its always good to check your system ...

---

### Post by jrssystemsnet on 2010-03-18
> **mohitchawla said:**
> However, when I booted into the OS, and started doing some web browsing, the system rebooted. This happened twice.

"Overclocked system" and "odd reboots for no apparent reason" go hand in hand.  If you want stability, don't overclock.  If you insist on overclocking, expect system instability (and plan on doing a LOT of testing to try to identify relatively stable values).

---

### Post by cascade9 on 2010-03-18
> **jrssystemsnet said:**
> "Overclocked system" and "odd reboots for no apparent reason" go hand in hand.  If you want stability, don't overclock.  If you insist on overclocking, expect system instability (and plan on doing a LOT of testing to try to identify relatively stable values).

Not always, I ran overclcoked for years with no issue. It was a minor overlcock, none of this 30%+ business, but still overclocked. 

Just overclocking the RAM shouldnt give any major issues, which is all that mohitchawla has done (and I would bet that he doesnt even know that its overclocked)

---

### Post by doas777 on 2010-03-18
how is your thermal looking, and does the shutdown seem to coincide with the usage of any particular device? 
I had a guy last week with a dying nic. every time he dialed up to dsl, it would work about 10 min before blackscreening (cause the nic pulled too much power).

personally I would suspect the ram or mobo, but I really can't recommend OCing. the performance boost is negligible, and is fraught with peril (and not fun peril like at the castle anthrax).

---

### Post by mohitchawla on 2010-03-18
Thanks for the replies folks. 

@cascade9: I know I was overclocking the RAM, by company settings I meant Corsair suggested settings. So that's not even hobbyist overclocking, just running the component at its designated specs ! 

And I haven't had other OC issues as such. Been running at 4GHz just fine. But I am waiting for a new PSU before going further.

Anyway, I have done enough passes of memtest86+ and a few hours of MPrime too...so most likely RAM is not faulty. The restart could also have been due to the nvidia blob. So, I am looking into that too.

---

### Post by cascade9 on 2010-03-19
It doesnt matter if the RAM is rated at 1333, its still an overclcock, and to run the RAM at 1333 with an i7 means either overclocking the blck (internal base clock) or uclk (uncore clock ratio). 

It wouldnt call a 25%+ overclock on anything 'small'. Not that you should have that many issues with a simple RAM overclock. 

If you were running @ 4GHz when it happened, I would think that it is your overclock. Running ANYTHING at a 50% overclock is way out of the envelope, and you are far more likely to get issues. Things like minor power blips that normally would do nothing can bring everything to a screaming halt. 

Of course, its always possibel that your nVidia blob did it, but I doubt it. If it was nVidia related, it would be the overclock that actually pushed things over the edge IMO.

---

### Post by soltanis on 2010-03-19
With all that overclocking going on, you might be cooking your system. It is possible that your RAM/processor is fine, but you are overheating your graphics card because of increased ambient heat.

Check your CPU/GPU temperature readings. If they redline and then you reboot, then there's your problem there. Otherwise, if your temp readings are fine but your random reboots are still happening, dial down your memory clock and see if that helps.

The performance boost you get from OCing your RAM isn't all that much anyway.

---

### Post by norseman-has-a-laptop on 2010-03-19
cool your system down to about 60-50 degrees and your cooking will be solved lol i over clock like none other with my cool system

---

### Post by mohitchawla on 2010-03-19
> **cascade9 said:**
> It doesnt matter if the RAM is rated at 1333, its still an overclcock, and to run the RAM at 1333 with an i7 means either overclocking the blck (internal base clock) or uclk (uncore clock ratio). 

It wouldnt call a 25%+ overclock on anything 'small'. Not that you should have that many issues with a simple RAM overclock. 

If you were running @ 4GHz when it happened, I would think that it is your overclock. Running ANYTHING at a 50% overclock is way out of the envelope, and you are far more likely to get issues. Things like minor power blips that normally would do nothing can bring everything to a screaming halt. 

Of course, its always possibel that your nVidia blob did it, but I doubt it. If it was nVidia related, it would be the overclock that actually pushed things over the edge IMO.

I wasn't running at 4 GHz then...I was just playing around with RAM multipliers. I can't have 4GHz with RAM at 1333 MHZ due to restriction on RAM multiplier (on the particular board, well...it IS a cheap board). So, that theory is out. 


@soltanis: Ambient temps are fine. GPU temps are in check. No problem there. 


@nohorseman: 32 at idle and 46-47 at load at stock freq. ain't hot.

---

### Post by doas777 on 2010-03-19
> **mohitchawla said:**
> I wasn't running at 4 GHz then...I was just playing around with RAM multipliers. I can't have 4GHz with RAM at 1333 MHZ due to restriction on RAM multiplier (on the particular board, well...it IS a cheap board). So, that theory is out. 


@soltanis: Ambient temps are fine. GPU temps are in check. No problem there. 


@nohorseman: 32 at idle and 46-47 at load at stock freq. ain't hot.


how beefy and how old is your power supply? do your voltages look right in lm-sensors?
the hardest thing to identify is a problem with the mobo or the cpu all you can really do to troubleshoot them is to eliminate everything else. I've replaced many more mobos in my day than cpu's or even ram chips (though one box did turn up dead ram last month). if you think it is a cheap board to begin with, then it's probably a good bet to just get a new one.

---

### Post by cascade9 on 2010-03-19
If it was just 2 minor restarts, I doubt you've got any major issues. I know, I'm like a borken reccord..but I've found power blips can do just what the OP had happen. Could be from the grid, could be house wiring, could be just something else starting/stoppign on the same circut- I have helped a friend figure out why his machine 'would restart several times in one night'. After a bit of testing his hardware, it turned out to be every time his fridge compresor turned on, the machine would restart LOL. I've also seen the same thing happen with a different person- that was his neighbour had a phase 3 kiln, it would randomly make his computer restart when it cycled on. 

If its still restarting for no apparent reason, then yeah, look at power supply/motherboard...or at least clocking it back down to stock (RAM and CPU) for testing.

---

### Post by doas777 on 2010-03-19
> **cascade9 said:**
> If it was just 2 minor restarts, I doubt you've got any major issues. I know, I'm like a borken reccord..but I've found power blips can do just what the OP had happen. Could be from the grid, could be house wiring, could be just something else starting/stoppign on the same circut- I have helped a friend figure out why his machine 'would restart several times in one night'. After a bit of testing his hardware, it turned out to be every time his fridge compresor turned on, the machine would restart LOL. I've also seen the same thing happen with a different person- that was his neighbour had a phase 3 kiln, it would randomly make his computer restart when it cycled on. 

If its still restarting for no apparent reason, then yeah, look at power supply/motherboard...or at least clocking it back down to stock (RAM and CPU) for testing.
you make a good point. if it's jsut one or two incidences, i would wait and see. when I have decided to replace a mobo in past, it's been after a month or more of bad acting, and extensive software side troubleshooting (reinstall drivers, check patches, and ultimately reinstall the os) before determining that it is a hardware issue (perhaps I'm just too cheap to pony up without being through).

---

### Post by cascade9 on 2010-03-19
LOL. 

Sometimes, you'd be suprised. My curent motherboard was having major issues, on booting I'd get a 'your previous attempt at overclcocking failed', going into BIOS' msg (or something like that). Not that I was overclocking. :|  I'd wait, and wait, and then wait a bit more...nuffin! Nada! Nill! It would never go into BIOS. I'd end up having to rip the side off the case and then do the clear  CMOS trick, and even that would only work 2 times out of 3. 

I tried flashing the BIOS to the newest version, changing all my drivers to the newest version.....then back to older versions...different OSes (winXP, win2K, various *nixes)....changing HDD, DVD, and I would have changed the RAM and CPU but I had no spares (and no money or else I would have bought a new board LOL). I was at wits end, and just about to try getting a new board....and then for no apparent reason it started working again, toally fine. I havent had the issue since. ;)

I'm just hoping that my 'good tester' system gets better soon (athlon 1200, 1GB DDR). I really like to have a system to play with distros on, and my 'bad' tester  is just to damn slow for most things (Compaq P3 866, 384MB) Plus its my downstairs media player, used for when I'm...er....having some *cough* 'chill time'  *cough* *looks from billowing smoke*. :D

---

### Post by mohitchawla on 2010-03-19
^^Woah, that's one heck of a success story ! :p

I feel you & doas777 are right...I haven't experienced the problem since then. Indeed it could just be a little power blip...and I hope it doesn't happen again. :)

---

### Post by doas777 on 2010-03-19
> **mohitchawla said:**
> ^^Woah, that's one heck of a success story ! :p

I feel you & doas777 are right...I haven't experienced the problem since then. Indeed it could just be a little power blip...and I hope it doesn't happen again. :)
if you can afford it, a UPS is a good investment(100-200usd). it protects your hardware from under/over voltage, reverse polarity, and dirty/noisy power. when configured it also can shut down your pc gracefully when power goes out, to prevent data loss or file system corruption. 

glad its staying stable for ya. cheers

---

### Post by mohitchawla on 2010-03-20
I don't know if this complicates things, but I do have a good UPS(APC) and did have it attached at the time this happened.

---

