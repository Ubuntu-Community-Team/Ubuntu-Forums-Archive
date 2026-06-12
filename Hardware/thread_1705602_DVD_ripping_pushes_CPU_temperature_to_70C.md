---
title: "DVD ripping pushes CPU temperature to 70C"
date: 2011-03-12
forum: Hardware
---

### Post by Keith_Beef on 2011-03-12
After upgrading to 10.10, I've noticed a problem with the CPU cores overheating when I use HandBrake to rip DVDs.

This was not a problem in 9.10; CPU core temps stayed below 60C, but now the temps go from an idle of around 37C - 40C with the fan at around 725 RPM straight up to 55C with the fan at 1000 RPM as soon as ripping begins, and get up to 70C (or occasionally even 74C) with the fan at 1400 RPM within two minutes.

Any idea why this is happening? or should I just bite the bullet and buy a better cooler than the stock Intel cooler that came with the CPU? I already have a case fan front and rear, no dust around, and good air flow.

K

---

### Post by Yellow Pasque on 2011-03-12
I remember another thread where a certain version of handbrake caused overheating. IIRC, the person used a different (newer?) version and the issue resolved itself.

---

### Post by Keith_Beef on 2011-03-13
> **Temüjin said:**
> I remember another thread where a certain version of handbrake caused overheating. IIRC, the person used a different (newer?) version and the issue resolved itself.

Thanks... I had done some searching, but for some reason or another hadn't found [the thread]("http://ubuntuforums.org/showthread.php?t=1646889") before I posted.

I took off the stock Intel heat sink and fan, cleaned the old thermal compound fron the CPU and the heat sink, and applied new Arctic Silver compound. 

This hasn't improved anything at all... the temperatures still shoot up to 70C quickly. I've been experimenting with burnp6, starting at an idle of 37C.
```
          core       0    1    2    3
one instance        53C  51C  57C  48C
two instances       64C  64C  65C  62C
```

I stopped with two instances running, because from time to time core 0 would shoot up to 77C.

So I reverted back to the Karmic version of Handbrake, which I had been using up until about a week ago, without ever encountering any overheating problems; the same this happens, straight up to over 70C. The same happens with AcidRip...

So something has happened here... is it possible that 10.10 is doing something that makes the processor work harder (no bad thing, if it means that ripping and encoding gets done more quickly)?

In any case, I suppose that this more or less demonstrates that the stock Intel cooler is insufficient, and that I should change it for something better. 

I have a Zalman on order from Amazon... 

[http://www.amazon.com/gp/product/B001P1B7B4](http://www.amazon.com/gp/product/B001P1B7B4)

I'll need to pull the mainboard out of the case to fit this, to fit the bracket on the underside, but anything has to be better than Intel's design for fixing the cooler to the board.

K.

---

### Post by Keith_Beef on 2011-03-14
> **optimizationguy said:**
> This sort of issue is quite common for [ripping dvd]("http://dvdrippingsoftwares.com/"), you can try other dvd ripper for alternative ...

I don't think you read my post quite well enough:
> 
So I reverted back to the Karmic version of Handbrake, which I had been using up until about a week ago, without ever encountering any overheating problems; the same this happens, straight up to over 70C. The same happens with AcidRip...

I'll try booting a live version of 9.10 sometime this week; I don't know  if I will be able to run burnp6 and watch temperatures from a live CD, but it is worth a try.

K.

---

### Post by Artemis3 on 2011-03-17
I have the feeling the older version wasn't using all your cores. 

Try this tool to stress your cpu, it should reach 70c the same.
[http://systester.sourceforge.net/](http://systester.sourceforge.net/)

If your processor has 2 cores + ht, use 4 threads; 4 cores + ht, use 8 threads, etc.

Applying thermal grease is quite tricky, usually just a very small drop in the center, more will cause heat :P

It is my experience that the intel stock fan is more than adequate for anything not involving overclock, unless there was a mistake putting it together.

First, no plastic covers between metal and cpu, thankfully those are very rare anymore (too many ppl leaving them on)...

Second, for the fancooler you must push REAL HARD in diagonal 2 at a time, until you hear the "click" sound on the four of them, and you can clearly see (under mobo) the black plastic tip coming out the white/transparent ones.

Test with your case open, and it should not go above 60c. See if your bios has any important fan throttle options.

I have experience with most intel processors, their stock fancooling works perfect. Even AMD's, tho these a little run hotter.

---

### Post by Yellow Pasque on 2011-03-17
The stock cooler fan should run at more than 1400RPM if the CPU is getting above 60C. Check your BIOS settings and check for BIOS updates for your mobo. If the BIOS can't control the fan properly, disable the BIOS fan control and then you can probably use the fan-control script.

> Even AMD's, tho these a little run hotter.
BTW, that's a gross over-generalization.

---

### Post by Keith_Beef on 2011-03-17
Well, I tried the 9.10 live CD, and managed to watch the temperatures while running burnP6...

As I mentioned a few days ago:
> I took off the stock Intel heat sink and fan, cleaned the old thermal compound from the CPU and the heat sink, and applied new Arctic Silver compound. 

With the case open, running 1, 2, 3 and then 4 instances of burnP6 steadily pushed the core temperatures back up towards 70C... I chickened out and killed off the instances when it reached 74C. The temperature quickly went back down to 40C - 44C.

I won't have any time to work on this again until the first week of April, by which time the new Zalman cooler that I have on order should have arrived. I'll take a lot more care over cleaning the CPU, and I'll try "tinting" the base of the heatsink, as explained in the Arctic Silver application guide.

[http://www.arcticsilver.com/pdf/appmeth/int/hl/intel_app_method_horizontal_line_v1.1.pdf](http://www.arcticsilver.com/pdf/appmeth/int/hl/intel_app_method_horizontal_line_v1.1.pdf)

Your comments, Temüjin and Artemis3, have been very helpful thank you.

K.

---

### Post by Keith_Beef on 2011-03-26
Today, I fitted the Zalman cooler that I mentioned in an earlier post.

I found that I must have put too much thermal compound on last time I refitted the Intel cooler, but also I think I might have at some point in time damaged one of the posts that fixes the cooler to the mainboard...

Three of the posts turned with a definite "click" to the release position, and I needed a little force to pull them up to release the pegs from the holes. But the fourth felt like there was no resistance when turning, and none again to pull it up to release.

So, I cleaned the CPU with isopropanol and then I "tinted" the heat sink contact surface, as indicated in the Arctic Silver guide. But I used the compound that was supplied with the Zalman heat sink. I don know what the shelf life is of Arctic Silver compound, but that has been sittin gin my desk drawer for at least two years.

It took me close to an hour and a half to fit the Zalman and re-assemble the whole computer. This is because I had to remove the mainboard from the case, which meant removing something like fifteen connectors, labelling each and photographing as I went, to make sure everything went back in the right place.

Then I connected to the rest of the peripherals and set four instances of burnp6 going... 

Joy.

Core temperatures were 39C, 39C, 40C, and 42C after leaving burnp6 running for ten minutes.

Idle temperatures were around 31C.

Ripping temperatures are around 40C to 45C, very slightly higher than burnp6.

---

