---
title: "Sweet spot performance/energy use/price"
date: 2009-10-23
forum: Hardware
---

### Post by clnanderson on 2009-10-23
Lots of stuff out there on performance/price, some stuff out there on energy use, but not as much looking at performance/energy/price use. So I'm looking to build a desktop that shows some nice performance increases over my previous machine (4 year old athlon 2 gig or so, video upgrade to nvidia 7600 a few years back). My usage is desktop 90% of the time, but I like to play some enemy territory, quake wars etc. No need for crazy video capabilities, but I like my frame rates high. 

On the other hand, I'd like to minimize power use in this machine. So I'm looking at

$170  AMD Phenom II X4 945 Deneb 3.0GHz Socket AM3 95W Quad-Core Processor 

$80  ASUS M4A77TD Pro AM3 AMD 770 ATX AMD Motherboard
  	
$95  PNY XLR8 VCG98GTEE5XEB GeForce 9800 GT EE 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card 

$85 G.SKILL 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Dual Channel Kit Desktop Memory Model F3-12800CL9D-4GBNQ

I'm looking at processor and video pulling 150 watts, throw in a couple of hard drives for another 40 watts and memory and mobo at maybe 50, and I'm hoping that this will be pulling a total of under 300 watts. (I could drop another 30 watts with a lower power quad core (65 watts)).

So questions I have:

1) Can I get by with a 380 watt psu, or should I go for something int 450-500 range? (I'm looking for at least an energy-80 bronze i think.

2) are the low power versions of the video and cpu really worth it? Or am I just fooling myself that I need a phenom quad + 9800gt, when cheaper less demanding hardware might pull the same power at a lower cost.

3) Any worries about compatibility I'm missing--I don't see anything, but hoping that if anyone's had bad experiences with something here, they'll chime in. I'm planning to use 9.10 64 bit.

---

### Post by cascade9 on 2009-10-23
Power  consuption is a tricky issue. It depends on who you  listen to. If you go to one of the online 'power supply calculators' it will tell you 400 watts+ for that setup. This site says 440-

[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

Then there are other places that will say other stuff. Xbit labs actually has a neat little test on real world, from the wall, power consumption, this is probably the closest thing in the test to what you have speced-

[http://www.xbitlabs.com/articles/coolers/display/system-wattage_6.html](http://www.xbitlabs.com/articles/coolers/display/system-wattage_6.html)

The Core2Duos are slighty more efficient than the X4s, but max power draw on that system is 189 watts! 

If it was me, I would be looking at a 450 or so, probably seasonic. Or something made by seasonic like a lot of the corsairs are, corsair HX520 would be my choice. But I'm biased, I own one ;)  It might be a bit more than you need, but its nice to have some wiggle room. 

As fro if that system is overkill....maybe. if your current 2Ghz (3000+ I guess?) + 7600 does the job, you wont need that much power. While dual or more cores wont help the framerate that much, the extra cache on the newer CPUs does help,a nd for desktop use more cores help, to a point. A friend of mine has a 3800+ (single core) and while my 4800+ (dua lcore) runs at the same speed, it is faster, especially for multitasking. 

BTW, from other threads I've seen around here, and on the net in general, you wont be able to use the 'full' 1600Mhz ram (and if you can its an overclcock anyway) 1333 might save a few $.

---

### Post by clnanderson on 2009-10-24
Thanks for the reply. Looks like DDR3 1333 and a Phenom II x3 gives me some price benefit, on memory and $70 on cpu). Beyond that it looks like it should run less than 200 watts idle and maybe 300 under load. So that suggests that 450-500 watts antec earthwatts bronze might be good enough, since I would hit the sweet spot of energy efficiency (50% load is 85% efficiency 25/75% looks like it's still above 82%). Looks like it would be about 10 watts if I upgraded to silver rating. But the price premium seems to be about $30-40. A 40% increase in cost and only probably around a 2-3% energy savings.

On the other hand I can save 30 watts on the cpu. by switching to the low power model of the same processor. Beyond that I'd have to go to a low power cpu (sempron, atom?) both of which give big performance hits.

Can't find any useful benchmarks comparing the low-power phenom II x3's and the black label edition, but the core speed drops from 2.8 to 2.5 I think, which seems like it would have a performance hit. Don't know whether the 30 watts is worth it. I'm thinking that it might be, since it is a 10% decrease in clock speed but a 30% decrease in power, cost is roughly the same.

Western digital's green drives seem to save around 5 watts over competitors. With two drives that might be 10 watts.

A few watts could be saved on lower voltage sticks of memory (some ddr3 seems to run on 1.65 volts, others down around 1.3 volts--though I read that each stick of memory draws about 2 watts, so the savings would be negligible.

If you want some 3d performance from a recent video card you cost yourself about 60 watts at least. But, as of now, I think I have maxed out performance while minimizing cost and energy.

Now I just need 9.10 to get out and I'll be good to go when the parts arrive.

---

### Post by cascade9 on 2009-10-26
I wouldnt go to the low power route myself. If you are really worried about power consumption, get a black edition x4 (unlocked) and then underclock and undervolt it. 

AFAIK, all the Phenom II CPUs are the same process (45nm) and any change in TDP is from core speed and voltage. Higher core speeds need higher voltage, and thats what makes the TDP higher on the fatsest models. You can get the same effect as from a 'low power' version from underclocking and/or undervolting. 

You might be able to play with the video card settings to drop power consumption as well. One reason to get a 9800 over a 9600, the 256bit memory bus + more pipelines mean you could lower the 9800 clock speed to the same as a 9600 and it shouls still be faster. 

On hdd- yes, the green power drives are low power. Neat little test here (start on this page, the next one, page 8, has more info)- 

[http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup_7.html](http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup_7.html)

Good luck with your new machine, hope you enjoy ;)

---

