---
title: "Overclocking &amp; Stability"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by ahaslam on 2007-02-23
Hi there,

I've just built a new desktop with an Intel Core2Duo E6300. I chose that intending to give it a mild OC, while keeping standard cooling (initially). I'm an OC n00b but I've increased the cpu frequency to 2135MHz (E6400 equiv.) & the DDR frequency has risen from 667 to 763MHz. So far, the CPU OC is quite conservative , with everything keeping nice & cool (with the case fan on slow). My worry is the RAM, that seems like quite an overclock for some 5400 @ 4-4-4-12.

Would you consider that safe? I seems to be & I wouldn't want to under clock my memory.
Is there anything that can test its stability other than memtest (which ran for 3 passes without issue)?

Additionally, do you know of any benchmarking apps? It would be nice to see what I've gained & where.


Tony ;)

PS. Does any of this actually help in games? I've not noticed much difference in Nexuiz, dropping down to 20fps at times.

---

### Post by kerry_s on 2007-02-23
-> [http://www.hardwarezone.com/articles/view.php?cid=2&id=2014](http://www.hardwarezone.com/articles/view.php?cid=2&id=2014)

---

### Post by ahaslam on 2007-02-24
Thank you, that's very reassuring for my cpu, showing a lot more potential. However it's the memory where my concerns lay. Maybe it would be safer to increase the FSB further & reduce the DDR multiplier? I just can't find any info on memory o/c'ing, so unless I fry my RAM I wouldn't know where the safe limit lays.

Tony.

PS. I don't have Windows, are there any linux benchmarking apps?

---

### Post by ahaslam on 2007-02-24
I now have the FSB set @ 333MHz, making the CPU run @ 2331MHz. This allows me to keep the memory at its default speed & vastly improves performance in games. This makes the CPU about 10°C warmer on stock cooling (with the case fan on slow), so I'll not push it any further for now ;)

If anyone knows of some good info regarding memory overclocks it would still be greatly appreciated, along with any recommended benchmark/stress test apps.

Tony :)

---

### Post by kerry_s on 2007-02-24
With over clocking there's always a risk somewhere. I have mine fully overclocked to 1.7ghz from the stock 1.2ghz, but i know my cpu has a limit of 2.0ghz, the limitation is my motherboard.

You at least know yours can do 3.36ghz from the article. Just remember once you've overclocked it you can't go back, it will burn in to that higher speed, if later you try and lower it it will be very unstable. For your memory you should see what the highest speed is(google), but it sounds like your doing it right, as in you raise the cpu and lower the for the memory. The thing that concerns me is you sound like your going straight to the highest you think you should do. You should instead do a little at a time and give it time to adjust(1 week). the longer you give it the better it'll run. so just raise it a little run it at that speed for a week, then a little more each week.

On my motherboard i have six settings, which i went up 1 by 1 each week, just using my feeling, no fancy tests, none of that crap, just everyday use. with my old ram when i got somewhere in the middle i had to lower the dram clock( can't remember, exact name) to bring the memory back to stable.

The important thing is to give it time and watch your temp, if it starts to act up, lower it and run it at that speed a little longer(1 month), then try again.

---

### Post by ahaslam on 2007-02-26
> Just remember once you've overclocked it you can't go back, it will burn in to that higher speed, if later you try and lower it it will be very unstable.
I hope that's only if you damage the chip during the oc'ing process, no performance loss here. 

I managed to bump it up to 2800MHz, but it required the case fan to be on high (too noisy for me). 
I have settled for the highest speed gained under minimal cooling, that being 2562MHz. This idles at 30°C and climbs to 50°C under full load. This doesn't rise the DDR freq. too much.

For temp monitoring I used lm_sensors with conky. To push the temp to the max I ran: cpuburn-in, glxgears & the BlockTube screensaver preview. The good thing about cpuburn-in is that it'll display any errors that were encountered during the test (none were encountered).

For performance benchmarking, I ran the Nexuiz timedemo with every setting at maximum. To run the timedemo, start Nexuiz, press shift&esc, and issue: 'timedemo /demos/demo1.dem' - this writes a benchlog file in your Nexuis data file. I get a very handy 10fps increase (av.), which really helps with online play.

Regarding memory, I still couldn't find any good info. But when I oc'd the cpu to 2.8GHz, ny ram was running at 800MHz & memtest86 reported no errors after many passes. As that's running at ddr2-6400 speeds, I doubt much more would be available & wouldn't consider going higher. I'm currently running it at 732MHz. 

Thanks for your advise. Overclocking is very intimidating tbw, but quickly becomes addictive.

Tony ;)

PS, here's a screenie (excuse the distro, Dapper wouldn't load):

[[img]http://xs112.xs.to/xs112/07091/stress.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs112&d=07091&f=stress.png)
[SIZE="1"]*The case fan is not pluged into the mobo, hence the reading*[/SIZE]

:)

---

### Post by kerry_s on 2007-02-26
> I hope that's only if you damage the chip during the oc'ing process, no performance loss here. 

No, that's from normal use the longer you run it at a certain speed, it wants to stay at that speed, but this is just a side affect of overclocking and will take along while. I have had mine overclocked for like 4 or 5 years, the thing is once you've overclocked you don't want to go back any ways. I thought i'd just let you know, i didn't find out till i tried to go back one time and it went wonky on me, i had no clue and there is little or no info about that, but apparently the avid overclockers knew, but don't say anything till asked and i guess it doesn't get asked that much. :)

---

### Post by ahaslam on 2007-02-27
Yeah, I'd not read of it before, though I suppose they say 'burn-in' for a reason ;)

I found that just running 2 instances of Mprime gets the system hotter than cpuburn-in & the rest, it also reports any errors. I also found some good info on core 2 duo temperatures [here]("http://forumz.tomshardware.com/hardware/Core-Duo-Temperature-Guide-ftopict221745.html"). Intels TAT wont run in wine, but lm_sensors seems to be quite accurate.

Tony ;)

---

### Post by kerry_s on 2007-02-27
Another thing you might want to do is jot down the over clocked settings and tape it inside your case just in case some day you have to reset the bios, like when replacing the battery or something. That away you can set it back exactly, instead of guessing or trying to remember. Ya, that got me when i redid my friends system, now i always put it, That way anyone who works on it can see the settings. :)

---

