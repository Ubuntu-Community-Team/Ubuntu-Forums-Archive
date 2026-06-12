---
title: "Trying to upgrade an old eMachines tower"
date: 2015-06-08
forum: Hardware
---

### Post by cwblanch on 2015-06-08
Hey,

As the title says I'm trying to upgrade an old eMachines tower that I've been given, but I have never built or messed with the internals of a desktop (aside from changing out RAM modules).

So I'm coming here for more info on how to change out the processor and video card and such. Also compatibility or if I need a new power supply for an upgrade like this.

The model of emachines is T3418. I've gotten my info on the computer [here]("http://www.cnet.com/products/emachines-t3418/specs/") and [here]("http://www.hardocp.com/article/2006/05/16/emachines_t3418/#.VXZSbc9Viko").

Is it worth is to put 4GB of RAM in this old desktop, I found on Amazon a 4GB package, but the page on CNET says its max is two, even though its a 64bit system.

I also searched [Amazon]("http://www.amazon.com/s/ref=nb_sb_noss_1?url=search-alias%3Daps&field-keywords=socket+754+processor&rh=i%3Aaps%2Ck%3Asocket+754+processor") for processors that would fit this motherboard, but I have no idea if any of the ones linked on that are an upgrade or will even work.

And the big upgrade I want for this is a video card. I would love to play games on this because, it may be old, but its probably an upgrade from my slightly aging laptop.
I have no idea what to look for in a budget video card that would work on a motherboard this old. I barely even know how to start looking for this. 
[This]("http://www.amazon.com/s?ie=UTF8&field-keywords=pci%20video%20card&index=blended&link_code=qs&tag=wwwcanoniccom-20") is as close as I've gotten. I would think a 1GB video card would be an upgrade from an integrated APU laptop ([Toshiba Satellite]("http://www.toshiba.com/us/computers/laptops/satellite/C850/C855D-S5109"))

Any help would be appreciated. I'm pretty excited to possibly upgrade from a laptop finally. Something that actually has dedicated graphics rather than integrated.
Hopefully this isn't too much to cover for newbie to hardware upgrades.

Thanks!

---

### Post by weatherman2 on 2015-06-09
I wouldn't spend a nickel on that old thing myself.  It looks to be 9+ years old, and it was a budget machine then, apparently.  On top of that, eMachines had a terrible reputation for poor reliability.  The power supplies were cheap in those old eMachines towers and would sometimes fail and take the motherboard with them.  The newer budget computers will be a lot faster than this old tower - I'd put any money you might spending upgrading this one toward a newer machine.

---

### Post by mamamia88 on 2015-06-09
Yeah I personally wouldn't spend a cent on that.  But, it could be a good learning experience for the future taking it apart.  That being said it looks like your socket 754 has some cheap cpus on ebay.   I have no idea if it would be worthwhile to do so though.  I hate to break it to you but you aren't gonna be playing any games on this

---

### Post by cwblanch on 2015-06-09
> **weatherman2 said:**
> I wouldn't spend a nickel on that old thing myself.  It looks to be 9+ years old, and it was a budget machine then, apparently.  On top of that, eMachines had a terrible reputation for poor reliability.  The power supplies were cheap in those old eMachines towers and would sometimes fail and take the motherboard with them.  The newer budget computers will be a lot faster than this old tower - I'd put any money you might spending upgrading this one toward a newer machine.


> **mamamia88 said:**
> Yeah I personally wouldn't spend a cent on that.  But, it could be a good learning experience for the future taking it apart.  That being said it looks like your socket 754 has some cheap cpus on ebay.   I have no idea if it would be worthwhile to do so though.  I hate to break it to you but you aren't gonna be playing any games on this


Alright, well I guess I'll just treat it as a learning experience for hardware and installing Ubuntu on an actual desktop.

---

### Post by tgalati4 on 2015-06-09
With only 2 GB, you will want to consider a ligher desktop environment such as LXDE, XFCE or MATE.  The motherboard chipset and the layout determines the maximum RAM.  Sometimes a BIOS update will allow more RAM, sometimes memory chip density will determine the maximum RAM that you can put in your machine.  You will have to search the web (extensively) to find other's experiences with RAM upgrades on that particular machine.

For a gaming rig, you will do better on craigslist and just buy a used gaming rig.  Gamers are constantly upgrading and dumping, so you can pick up some decent hardware at a significant savings.

---

### Post by mörgæs on 2015-06-09
The best foundation for a thread like this is stating the hardware specifications, that is the specifications of your particular computer. Googling the name of the machine is not enough.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Yellow Pasque on 2015-06-10
^Usually, I like a lshw listing too, but the second link the OP gave has good specs/pics.

I wouldn't even bother looking for a CPU upgrade. There are only a handful of Socket 754 models that are (slightly) faster than the 2.0 GHz Sempron 3400 already in the machine, and who knows if the BIOS supports them.

> Is it worth is to put 4GB of RAM in this old desktop, I found on Amazon a 4GB package, but the page on CNET says its max is two, even though its a 64bit system.
I would usually take cnet specs with a grain of salt. In this case, there are only 2 RAM slots, and I don't think Socket 754 CPU's support 2GB sticks, so I would assume 2GB total is the maximum supported.

> And the big upgrade I want for this is a video card.
I wouldn't spend too much money on a GPU for this system, or you're going to hit the point of diminishing returns where the CPU bottlenecks you significantly.  You've got a PCI-e x16 slot, so that's good. It's probably a PCI-e 1.0 slot, so I don't think I'd try for any GPU too modern. Something like a RadeonHD 4770 seems ideal to me, or maybe a GTS450 if your PSU can handle it.

> I wouldn't spend a nickel on that old thing myself.
A lot of it depends on the PSU, so if it's cheap and doesn't leave room for upgrading as you speculate, you may be correct. However, I think a cheap GPU upgrade could be worthwhile, depending on what apps/games the OP has in mind. The CPU is not bad compared to the Pentium 4's that a lot of machines from this era have. Also, I think this system was made a bit after the "failing capacitor" era.

---

### Post by Yellow Pasque on 2015-06-10
So a little googling on the model shows it probably has an em-2436 power supply and may only have a single 12V rail that ca give 16A. That's probably not enough for a GTS450. I can't find amperage numbers for the 4770.

---

### Post by mörgæs on 2015-06-10
The lshw output is necessary because we don't know what has been changed in the computer. CPU, GPU and size of RAM could all have been modified without we (or original poster) knowing.

---

### Post by Yellow Pasque on 2015-06-10
^Aye Cap'n. I like lshw too.

---

