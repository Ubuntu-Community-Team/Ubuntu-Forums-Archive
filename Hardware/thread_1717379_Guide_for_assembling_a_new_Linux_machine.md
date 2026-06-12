---
title: "Guide for assembling a new Linux machine?"
date: 2011-03-29
forum: Hardware
---

### Post by Rocks and Water on 2011-03-29
I happily made the switch to ubuntu a couple years ago. I'm now in the process of getting a new desktop and I'm contemplating assembling it myself as a fun project. Having never done this before, I'd like to read up as much as possible before taking the plunge. Can anyone recommend some PC building guides for newbs like me? Preferably one geared towards linux users if possible?

---

### Post by Dark_Stang on 2011-03-29
I don't really have any recommendations for books or reference material, but I have a few pointers...

1. Make sure the hardware you're looking at is Linux compatible. Especially the little things, like network cards.
2. You still get more bang for your buck with AMD these days. For the cost of a nice Intel i7 machine you can build 2 nice AMD Phenom II X4 machines.
3. Get a decent video card, they're relatively cheap anyway.
4. Always get a slightly more powerful video card than what you need. If I calculate that I'll need 400w of power, I'll get a 450-500w power supply.
5. If you plan on running virtual machines get a ridiculous amount of RAM. My home laptop only has 4GB, but I don't run an VMs on it. But my PC at work has 12GB of RAM so I can run 3 virtual machines at once (and of course the native OS) and give each machine 4GB each.

---

### Post by Rocks and Water on 2011-03-29
Thanks Dark_Stang. That all sounds like good advice. I'll definitely be checking with people on this forum to make sure all my parts are linux compatible.

What I really have no idea how to do, however, is physically assemble the computer. Does anyone know of any easy to understand guides or reference material that would be of help?

Also, you suggest buying AMD over Intel. Does one generally work better over the other with linux? So far, I was thinking of going with the Intel Core i5 2500K. I noticed that it is used by System76 (I assume that they know what they're doing) and it was reviewed quite positively on [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2500k&num=1").

---

### Post by Dark_Stang on 2011-03-29
> **Rocks and Water said:**
> What I really have no idea how to do, however, is physically assemble the computer. Does anyone know of any easy to understand guides or reference material that would be of help?
The physical assembly is quite easy. Just make sure you're well grounded so you don't harm any of the parts, and always touch the sides of the cards not the tops and bottoms of them. As long as you pick out the proper parts everything will just slide, slip, and snap into place. If you're looking for specific guides there are tonnes on youtube.
[http://www.youtube.com/results?search_query=build+your+own+computer&aq=f](http://www.youtube.com/results?search_query=build+your+own+computer&aq=f) 
But my best suggestion is to have somebody there with you that's done this before.

> **Rocks and Water said:**
> Also, you suggest buying AMD over Intel. Does one generally work better over the other with linux? So far, I was thinking of going with the Intel Core i5 2500K. I noticed that it is used by System76 (I assume that they know what they're doing) and it was reviewed quite positively on [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=intel_corei5_2500k&num=1").
No, one isn't more compatible with Linux than the other. The laptop I'm on right now is running an i3, my fiance's desktop that she just built runs a Phenom, my work machine is an i5, and my media center is an older Athlon X2. But when you build you can generally find much better deals on AMD processors and on motherboards with AMD sockets.

---

### Post by Rocks and Water on 2011-03-29
Unfortunately, I don't know of anyone who can help me with assembly (I don't have many computer geek friends familiar with hardware), so I'll have to rely on online guides for that.

How do you go about choosing a motherboard and sockets that match the processor? For example, what would you suggest using for a Intel Core i5 2500K or the AMD Phenom II X4 that you recommended?

---

### Post by d106550 on 2011-03-29
Physical assembly these days is not an issue anymore. Everything is plug and play. However I must admit it's been a while since I've assembled a computer myself especially since I did away with my last desktop a few years ago now.

The most important thing is to check if all parts you are ordering are supporting each other. I would spend to most time of all researching what RAM to use. This is usually the bottleneck of your system and could run you into some serious problems if you end up with inconsistencies. 

Other than that: basically the newer your hardware the bigger the chance of linux not having caught on yet.

---

### Post by Rocks and Water on 2011-03-29
> **d106550 said:**
> Other than that: basically the newer your hardware the bigger the chance of linux not having caught on yet.

That seems like the hard part. Finding parts that are new, but not TOO new that they lack support.

---

### Post by Dark_Stang on 2011-03-29
The i5 2500k uses a LGA 1155 socket. So if you're going with that processor you'll want to find a motherboard with an LGA 1155 socket for it. Now here is where price comes in...
Intel i5 2500k - $225
Decent Asus ATX motherboard - $145
[Link to motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131706")

But if we look at AMD...
AMD Phenom II X6 1090T Black Edition - $200 (2 more cores, $25 less than the i5)
More than Decent Asus ATX Motherboard - $150
[Link to Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849")
[Link to Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131631")

---

### Post by Rocks and Water on 2011-03-29
Thanks Dark_Stang, that's really helpful.

How does one go about choosing a power supply, as well as fans and cooling? My current desktop is extremely loud, so reducing noise and getting it as reasonably silent as possible would be great.

---

### Post by Dark_Stang on 2011-03-29
> **Rocks and Water said:**
> Thanks Dark_Stang, that's really helpful.

How does one go about choosing a power supply, as well as fans and cooling? My current desktop is extremely loud, so reducing noise and getting it as reasonably silent as possible would be great.

Choose your power supply last, as you'll need to know how much power you'll be consuming before you pick one out. But this is pretty easy. You just need to see how much power all your parts take. Most desktop processors will be using 80-125w. High end graphics cards can consume loads of power, so watch out for these. They should list either power consumption or minimum recommended power output for a power supply. Minor parts (network cards, normal cards, etc) don't use hardly any power. And I usually chose a power supply with a large fan to help with cooling.

The bigger the fan is the slower it needs to spin to keep the parts cool. My fiance's new build uses 1 120mm fans on the case, 1 120mm fan in the PSU, and 1 90mm fan on the CPU and it's super quiet. My laptop is actually louder. The two loudest fans in a desktop will be the CPU fan and the graphics card fan as they can spin much faster than the case fans. There are passive heat sinks (no fans) that you can use for your video card and processor, but I've never used one as I'm paranoid about them.

---

### Post by Rocks and Water on 2011-03-29
> **d106550 said:**
> The most important thing is to check if all parts you are ordering are supporting each other. I would spend to most time of all researching what RAM to use. This is usually the bottleneck of your system and could run you into some serious problems if you end up with inconsistencies.

How do you know which RAM to use?

---

### Post by Dark_Stang on 2011-03-29
> **Rocks and Water said:**
> How do you know which RAM to use?

By looking at what RAM dimms (slots) are on the motherboard. Almost everything out there is going to be DDR3. Then you'll just want to get the fastest memory your motherboard (or your wallet) can handle. Most motherboards will use DDR3 1066 or 1333 memory. The nicer ones will go higher.

---

### Post by collisionystm on 2011-03-29
Just think about what you want to do with the computer and base off of that. Dont worry about Intel vs AMD. This day and age they are all good and really none is better than the other. Intel runs a cooler temp than AMD and that is just common knowledge. However AMD is cheaper because they are the competitive underdog trying to find a place in the market again. Intel and Nvidia have done alot of taking over. Browse Newegg.com and find a barebones case that already includes a motherboard. I am not sure where you live but you should also look to see if there is a Micro Center near you. That is by far the BEST place to go for computer parts... its the size of a toys r us with nothing but computers computers and computer parts. I would get a quad core processor and if you are not doing any heavy apps or video design, 4 GB is more than enough ram for a linux machine. 
Nvidia video cards are very nice. I have not used ATI (now amd) in a long time. As far as 'Linux compatible' hardware, I have not seen anything that ubuntu cannot use right out of the box except for wireless cards. Everything else follows a pretty generic scheme. Before purchasing a video card, just do a google search for ubuntu <manufactureofvideocard> <model> and see if anyone has already tried it. Get a good 750 watt power supply. It is always good to have more power to your hardware. I would not water cool the computer... although I have had one and it was cool at the time... it is a hassle to move around and you will always have a fear in the back of your mind that you may spring a leak all over your new motherboard! Other than that stuff... don't worry to much. You will be fine!

---

### Post by oldfred on 2011-03-30
I like to look at several sites that do system builds. I never use exactly one of them but like to read the comments as they discuss the issues.

This regularly does three different price points:
[http://www.tomshardware.com/reviews/build-a-pc-cpu-overclock-best-compouter-component,2902.html](http://www.tomshardware.com/reviews/build-a-pc-cpu-overclock-best-compouter-component,2902.html)
[http://www.tomshardware.com/theme-build-your-own,156.html](http://www.tomshardware.com/theme-build-your-own,156.html)

[http://www.silentpcreview.com/section21.html](http://www.silentpcreview.com/section21.html)

Tom's also has a comparison of Video cards and "best" at each price point. Since I am not a gamer I look at $100 or less or last year's more expensive one's. Last page of one of these has a comparison by vendor & performance.
[http://www.tomshardware.com/charts/graphics-cards,1.html](http://www.tomshardware.com/charts/graphics-cards,1.html)

One of several power supply calculators. I always have to be generous with the numbers these calculate, but you do not want to go too large unless you plan major expansions later.
[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

---

### Post by mastablasta on 2011-03-30
regarding assembly - good mothebroard manufacturers will provide you with detailed guide on where goes what. and it will also include BIOS manual and how to set up the computer.
 
as it was mentioned you need to know first what you will use the computer for. if it's occasionaly movie, some internet browsing etc. then you don't need something fast. instead something with lower energy output is better.

---

### Post by galacticaboy on 2011-03-30
I do not know about anyone else, but my dream machine would be a 1TB Hard Drive with 4GB Ram, GerForece GTX 590 GPU, BIG LCD Monitor, Wireless Keyboard, Wireless Mouse, Wireless Graphics Tablet, Multiple USB Ports, CD DVD RW Combo Burner, Multimedia Card Reader, with Surround Sound Speaker system with a Subwoofer! I would love that, the ultimate Ubuntu Power PC with Surround sound and enough graphics to see the detail in a piece of sand with Google Earth. Just a dream!


But I am stuck with a
Pentium 4
512 MB Ram
20G Hard Drive
With Intel on board graphics...
David

---

