---
title: "Is it my power supply or something else?"
date: 2010-05-24
forum: Hardware
---

### Post by rcayea on 2010-05-24
My question as the title of this thread pertains to is, any time I increase my CPU voltage, even increasing it the most minimal amount, my computer doesn't boot past the screen that tells me my overclocking has failed. Do you think this is a CPU issue, a mobo issue, or a power supply issue?

Motherboard: Asus P5q SE2
Powersupply: Antec 550 powersaver
CPU: Intel E7400 stock speed: 2.80, currently 3.05.

Thanks,
Randy

---

### Post by Grenage on 2010-05-24
It's not really a 'problem' if things are running fine at stock levels, but I would suspect the CPU.

---

### Post by Linuxforall on 2010-05-24
ASUS is a good board so its not the MB and Antec is a quality PSU maker so thats not the issue here either. Are you using AI overclocking in ASUS BIOS?

---

### Post by rcayea on 2010-05-24
> **Linuxforall said:**
> ASUS is a good board so its not the MB and Antec is a quality PSU maker so thats not the issue here either. Are you using AI overclocking in ASUS BIOS?

I could never get Asus's graphical helper to work with WINE or any other program. 

I have done all my tweaking from the BIOS. 

Since the replies seem to think it is the CPU, could the CPU just not be able to pushed any more? I ask because I have read plenty of other forum posts where people have pushed this CPU to 3.3 and 3.4.  I do have sufficient cooling, too. I have the Zalman 9700 and it works great.

---

### Post by Linuxforall on 2010-05-24
I think it could be RAM as many don't like to be pushed any higher in bus speed.

---

### Post by rcayea on 2010-05-24
> **Linuxforall said:**
> I think it could be RAM as many don't like to be pushed any higher in bus speed.

Could it be that no matter how much RAM I have (I have 5GB) that it doesn't matter how much more I add? I am running 64bit.

---

### Post by rcayea on 2010-05-24
> **Linuxforall said:**
> I think it could be RAM as many don't like to be pushed any higher in bus speed.

With my mobo RAM is tweakable. I haven't totally dove into tweaking it but maybe I should look into that first. By not total I mean, I have tried changing from 5-5-5-14 (i think it was) to 5-5-5-18 and that got me the same result as my other problem - a no boot. 

Thanks for your information.

---

### Post by cascade9 on 2010-05-24
> **Linuxforall said:**
> ASUS is a good board so its not the MB and Antec is a quality PSU maker so thats not the issue here either. Are you using AI overclocking in ASUS BIOS?

Never assume that. Asus has made some good boards.....they have also made some awful ones.  Same with Antec and power supplies. 

> **rcayea said:**
> I could never get Asus's graphical helper to work with WINE or any other program. 

I have done all my tweaking from the BIOS. 

Since the replies seem to think it is the CPU, could the CPU just not be able to pushed any more? I ask because I have read plenty of other forum posts where people have pushed this CPU to 3.3 and 3.4.  I do have sufficient cooling, too. I have the Zalman 9700 and it works great.

Well, its not 'this' CPU, but one of the same type. Overclocking isnt an exact science (its not that much of science anywayLOL). Just because other Intel E7XXX CPUs have overclocked to X.XGhz, doesnt mean that the one you have will. 

It could be your CPU just cant be pushed any harder, or there is something not setup right in the BIOS, there are a lot of tweakable options. Have a look at the settings here- 

[http://www.overclock.net/intel-motherboards/418647-asus-p5q-se2-2.html](http://www.overclock.net/intel-motherboards/418647-asus-p5q-se2-2.html)

BTW, the screen screenshots there have a E7200 @ 3.72Ghz. ;)

---

### Post by Grenage on 2010-05-24
> **rcayea said:**
> I have read plenty of other forum posts where people have pushed this CPU to 3.3 and 3.4.  I do have sufficient cooling, too. I have the Zalman 9700 and it works great.

When it comes to overclocking, result vary wildly on the same chip type.

---

### Post by SlugSlug on 2010-05-24
bump up ram V

---

### Post by mr clark25 on 2010-05-24
i really want to see if this leads to anything!

the one thing knowone has asked for yet...  how many watt is your PSU?

---

### Post by cascade9 on 2010-05-24
> **mr clark25 said:**
> i really want to see if this leads to anything!

the one thing knowone has asked for yet...  how many watt is your PSU?

Already answered, 1st post-

> **rcayea said:**
> Powersupply: Antec 550 powersaver

---

### Post by dino99 on 2010-05-24
calculate the power needed:

[http://support.asus.com/PowerSupplyCalculator/PowerSupplyCalculator_right.aspx](http://support.asus.com/PowerSupplyCalculator/PowerSupplyCalculator_right.aspx)

---

### Post by Yellow Pasque on 2010-05-24
Unless you have multiple GPU's or a real power hog of a video card, then an Antec 550W is more than sufficient power-wise. It's possible you have a poor-quality CPU sample, at least in terms of OC'ing, but more likely, your RAM is OC'd too far. You may need to raise the RAM voltage or use a (different) memory divider to keep increasing the FSB. What is your RAM rated at?

Quick google shows e7400 uses a 10.5 multiplier and 266MHz base clock for the FSB. Since you're running at 3.05GHz, I assume you have the FSB raised to 290MHz. If you're running DDR2-800 RAM and you left the RAM divider at 2:3 (DDR2-800), you're now running the RAM at 435MHz (870 DDR). If that's the case, try selecting a lower RAM divider (i.e select your RAM speed as DDR2-667 for a 4:5 divider). That will give you another 30MHz to play with on the FSB (for 3.36 GHz on the CPU) without OC'ing the RAM.

---

### Post by rcayea on 2010-05-24
Thanks everyone for the information. I am heading home from work now and will report if any tips have helped. 

I was always hesitant about overclocking RAM. I have read that it is too difficult for what you get out of it and that it is easy to over-do-it, as in fry the RAM or even the CPU.

---

### Post by rcayea on 2010-05-24
> **Temüjin said:**
> Unless you have multiple GPU's or a real power hog of a video card, then an Antec 550W is more than sufficient power-wise. It's possible you have a poor-quality CPU sample, at least in terms of OC'ing, but more likely, your RAM is OC'd too far. You may need to raise the RAM voltage or use a (different) memory divider to keep increasing the FSB. What is your RAM rated at?

Quick google shows e7400 uses a 10.5 multiplier and 266MHz base clock for the FSB. Since you're running at 3.05GHz, I assume you have the FSB raised to 290MHz. If you're running DDR2-800 RAM and you left the RAM divider at 2:3 (DDR2-800), you're now running the RAM at 435MHz (870 DDR). If that's the case, try selecting a lower RAM divider (i.e select your RAM speed as DDR2-667 for a 4:5 divider). That will give you another 30MHz to play with on the FSB (for 3.36 GHz on the CPU) without OC'ing the RAM.

WOW! Great info. Thanks. Will try and let you know what happens. I did not know about RAM divider. So far I have only attempted to increase the 266mhz -> 305.

---

### Post by rcayea on 2010-05-25
With this link and the tweaks in the pictures provided by Cascade9: [http://www.overclock.net/intel-mothe...p5q-se2-2.html](http://www.overclock.net/intel-mothe...p5q-se2-2.html)
and a bit of tweaking I have successfully boosted my cpu. My proof is in the picture I attached. Before the picture I was running about 3.05-3.07 or so, now as the picture suggest, I am at 3.36. Thanks to all for the help. I simply wanted to speedup the CPU and well, by-golly, this forum kicks rear end.

THANKS!

---

### Post by rcayea on 2010-05-25
OK. So, for the last four hours or so I have been clocked at 3.52. I know four hours isn't much of a sample, but my computer has been very stable. I'm not sure if I want to try to push this thing any further. We'll see if I get brave.

---

### Post by tgalati4 on 2010-05-25
I would say that's a decent overclock.  Run memtest overnight and get 30 complete cycles on your RAM.  If your RAM passes at the higher speed, and you have sufficient thermal monitoring on the CPU, then you should be OK at the higher speed.

---

### Post by SlugSlug on 2010-05-26
Do you actually see any difference than from running it at stock?

---

### Post by rcayea on 2010-05-26
I do, yes. As someone who is in front of his computer many hours a week, I notice a difference especially when I am compressing/uncompressing. And, I also see a difference when I click on something. Everything just happens faster. I can understand for someone who may just use a computer to use the internet may not notice, but I have a great interest in computers and feel that I see the difference.

---

### Post by cascade9 on 2010-05-26
Not everybody would, but I'd notice a 20-25% overclockeasy. I notice the difference on less than that. :) 

> **rcayea said:**
> With this link and the tweaks in the pictures provided by Cascade9: [http://www.overclock.net/intel-mothe...p5q-se2-2.html](http://www.overclock.net/intel-mothe...p5q-se2-2.html)
and a bit of tweaking I have successfully boosted my cpu. My proof is in the picture I attached. Before the picture I was running about 3.05-3.07 or so, now as the picture suggest, I am at 3.36. Thanks to all for the help. I simply wanted to speedup the CPU and well, by-golly, this forum kicks rear end.

THANKS!

Woohoo! It worked. ;) 

I'm glad that link helped ;)

---

### Post by mr clark25 on 2010-05-27
you are testing for stability, right?

if not you need to.

if you are, what are you using? i made a moderately usefull script that uses pi to stress your cpu...

how are you doing temperature wise under load?

my website with my "pi stress" script-  mrclark.ath.cx/linux/linux/mypi.html

---

### Post by rcayea on 2010-06-07
> **mr clark25 said:**
> you are testing for stability, right?

if not you need to.

if you are, what are you using? i made a moderately usefull script that uses pi to stress your cpu...

how are you doing temperature wise under load?

my website with my "pi stress" script-  mrclark.ath.cx/linux/linux/mypi.html

Under load, my temps are about 32-35 degrees. I would love to try the script. I will give it a go soon and report back. thanks, Randy

---

### Post by Bowenbilt on 2010-06-08
> **rcayea said:**
> My question as the title of this thread pertains to is, any time I increase my CPU voltage, even increasing it the most minimal amount, my computer doesn't boot past the screen that tells me my overclocking has failed. Do you think this is a CPU issue, a mobo issue, or a power supply issue?

Motherboard: Asus P5q SE2
Powersupply: Antec 550 powersaver
CPU: Intel E7400 stock speed: 2.80, currently 3.05.

Thanks,
Randy
Personally, The biggest problem may be the CPU.

---

### Post by cascade9 on 2010-06-08
> **Bowenbilt said:**
> Personally, The biggest problem may be the CPU.

Considering that rcayea got his (her? never know) overclock working, the CPU is fine ;)

---

