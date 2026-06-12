---
title: "how to tell if system overheated"
date: 2010-04-29
forum: Hardware
---

### Post by foxbeard on 2010-04-29
I'm running 9.10 on a home-built rig with a Athlon 64 x2 5000CPU  on an                               [                              ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813130182")MSI K9N2G Neo-FD mobo.
Lately, for school, I've been running a program that uses both cores at 100% and needs to run for about a solid week. (It's training a Neural Net to play checkers, if anyone is wondering).
However, it seems to run for about an hour or so before abruptly shutting down. I suspect it is shutting down because it is hitting the critical heat level (100 C), as I've noticed the temp gauge I have on my desktop floats in the high 90s when running like this.
It should not be doing this (It's not overclocked, just running at maximum capacity, which should, ideally, be fine), and I think that my mobo may be reporting inaccurate temps. I have a decent after market heatsink and fan (I've had problems with AMD stock heatsinks in the past), and the inside of the case has clear airflow. The case has about 6" clearance from the wall. Admittedly, my apartment does get warm during the day (this is Alaska, we don't have AC in cheap apartments here).
Any thoughts / ideas on why it's running so hot?

Anyway, I've dug through every log file I know of to see if the OS initiated the shutdown, and haven't found anything out of the ordinary.

As a stopgap solution, I've disabled multi-threading in the code, and it seems to be keeping cool enough when only running one core at a time. The problem is that this doubles the runtime, and the project due date is fast approaching. 

My question is, what does Ubuntu do/log when the critical temperature is reached?
Also, knowing that this is a BAD idea, is there a way to disable the auto-shutdown, or at least change the critical temp?

It may also be the mobo initiating the shutdown (which would be unfortunate because I see no options in the BIOS to disable. change the shutdown temp).

---

### Post by madverb on 2010-04-29
I don't think Ubuntu does anything.
The motherboard will shutdown when over a certain temp.
Since it is a custom built box and running at high 90's I would be looking into why that is. That is an extreme temp for a CPU even on full load.
Maybe purchase a better heatsink/fan setup.

---

### Post by gradinaruvasile on 2010-04-29
It is not normal that your CPU has that kind of temperature - it must be some cooling problems.

Check the cooler's fan if it is really working at its full speed, blow out the dust from the case and clean the heatsink. Be very careful, the 90-100 C is the upper limit of functioning temperature and it damages the CPU if kept for longer periods.
It MAY be incorrectly reported but if it isnt, you probably will end up with a fried CPU. I have seen it before with malfunctioning coolers.

I personally used my Athlon 3200+ for gaming (i think it was on full load in Oblivion/Medieval Total War and games of the like on Wine) for 6-10 hours and never got to 65 C as far as i remember. I used stock cooler BTW.

---

### Post by cascade9 on 2010-04-29
High 90s (C)? Too hot. OK....theres a few things that could be happening here. 

Is your case dusty? Heatsinks with a nice layer of dust on the fins, or the fan, tend to run a lot hotter. 

If its not dusty, is there much airflow though the case? Computer that will run fine with no cases fans, etc, at normal loads can get very hot, very quicky if run at high loads for any length of time with not enough airflow though the case. The old 'down and dirty' solution is to take the sides off the case, and set a desktop fan to blow into the case. If it still runs hot like that, then its not an airflow problem. 

I'll assume you have a decent heatsink (just because its an aftermarket heatsink doesnt make it that much better than the AMD version). I would guess that your setup is a few years old? It could be that your thermal paste has 'cooked' (lost all the 'wetness' that the thermal paste needs to transfer heat). If the thermal paste is 'cooked' it will act like a blanket and keep heat in. A cheapo tube of silicon grease (thermal goop) will work, but getting a slightly better thermal compound like artic silver is a good iea- not that much more money but better heat transfer (and it tends to keep its 'wetness' longer than cheap silicon grease). 

Really..you dont want to change the thermal shutdown point, even if it is possible. (it should be, somewhere). 

Another solution is to get a new CPU- a nice Phenom 9850 (qaud core) that runs in your motherboard would only cost you about $85 from newegg, and get the work done a loty faster. I dont know if that is something you want, or can aford to do though.

---

### Post by foxbeard on 2010-04-29
Thanks for the input.
There's not much I can do at the moment, but when it finishes running I'll crack it open and clean the dust and re seat the heatsink with new thermal grease. Hopefully that will make a difference. Do you know if there is a shelf life for thermal grease? My rig is only about 1.5 years old,  but the grease I used was leftover from my former build that I've had for about 6 years now. It's been kept in a little syringe, with the tip capped off, and hadn't seemed to dry out. There's wasn't enough left after this build to keep, so I'll be getting some new stuff anyway, but I'm just curious. 

I lowered the search depth on the program, so it will complete in time running single threaded. I think I should still be able to get usable results.

---

### Post by cascade9 on 2010-04-29
> **foxbeard said:**
> Do you know if there is a shelf life for thermal grease? My rig is only about 1.5 years old,  but the grease I used was leftover from my former build that I've had for about 6 years now. It's been kept in a little syringe, with the tip capped off, and hadn't seemed to dry out. 

Provided that its kept in the right conditions (ie not very hot, room temp should be fine) thearmal grease should last years (probably even decades) on the shelf....I'm still using the Aritic Silver I bought in 2002. 

Just because it was still 'good' wont stop it from drying out though. Cheap thermal grease cooking to 'bad' is something I've seen happen pretty quickly (within a year with cheap stuff).

---

