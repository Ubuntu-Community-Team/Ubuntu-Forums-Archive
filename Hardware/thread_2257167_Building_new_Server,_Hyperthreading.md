---
title: "Building new Server, Hyperthreading?"
date: 2014-12-17
forum: Hardware
---

### Post by p2ranger on 2014-12-17
I'm planning to replace my server which is currently [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012"):
[COLOR=#000000][FONT=Verdana]
Foxconn R10-S4[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Intel Atom 330 dual core[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2 GB Ram[/FONT][/COLOR]

I'm looking at the i core Intel chips and wondering if it will be worth it or not to buy an i7 over an i5.

Intended uses:
[LIST]
[*]Media streaming with Subsonic and Serviio (both use Java)
[*]Samba file shares
[*]Owncloud
[*]Web server (photo gallery mainly for family members)
[*]Print server
[*]Backuppc for backing up local computers
[*]Crashplan for offsite backups (uses Java)
[*]Transmission BT
[*]Bittorrent Sync
[*]Mumble (voice chat)
[/LIST]

Currently my server reaches CPU saturation when either backuppc is running or is one of the Java programs is being asked a lot of. FFMPEG does transcoding of the media streaming services.

Mostly what I see people talking about Hyper Threading helping out is for people doing video editing. Would I get any benefit or would an i5 do just as well

Thanks

Jason

---

### Post by weatherman2 on 2014-12-17
Yeah, I had a 330 server for a long time as well.  Very slow but good for light-duty use.

An i5 will probably be 10X faster or more than that ancient Atom, maybe 20X faster.  I highly doubt you'll see much benefit from an i7 unless your sever will do not only those things you mention but will also have several users at any one time and so potentially be heavily loaded.

Hyperthreading is simply adding an extra logical CPU for the operating system to schedule.  Internally, hyperthreading duplicates some parts of a core so you kind of get two cores - but not really.  It's not the same has having an extra CPU - maybe half of one.  It gives you some performance benefit in some circumstances.  A dual core CPU without hyperthreading will be faster than a single core CPU with hyperthreading.  A quad core CPU with hyperthreading would have eight logical CPUs though as I said it's not really the same as having eight cores.  There's a point of diminishing returns with more logical CPUs anyway, depending on how your tasks can be split up.  A server serving multiple users doing multiple things would definitely benefit from hyperthreading, at least somewhat.  With one user, doing one thing - the software would need to be designed to split up that one task into multiple processes to benefit from multiple CPUs.

But can you even get an i5 or i7 without hyperthreading?  I think most of them have it.  An i7 may have more cores, larger cache, etc. than an i5.  Even an i3 has hyperthreading.

To compare CPUs, look up their CPU benchmark in a search engine and compare them.

---

### Post by p2ranger on 2014-12-17
Thanks for the input.

The i5's do not have hyperthreading. That and increased cache are the benefits to the i7's. The i5's and most i7's have 4 cores. The outrageously priced i7's have more cores, but I can't justify that price for a home server.

I've been struggling to understand if any of the software I run would significantly benefit from hyper threading. The way I understood it is its like eating. The mouth is the CPU core. You have two hands and one mouth. Non hyperthreading is eating with one hand. Hyperthreading is like eating with two hands. I think I'll just save the extra money for the i7 to go towards the new desktop I want.

I'm planning to turn my old server into a Pfsense box.

Thanks

Jason

---

### Post by Yellow Pasque on 2014-12-18
> I've been struggling to understand if any of the software I run would significantly benefit from hyper threading

HT can boost heavily multi-threaded tasks like encoding. Are your specific tasks so demanding that a quad core i5 couldn't handle them? It's hard to say when all you have to compare it to is a dual-core Atom.

>  The way I understood it is its like eating. The mouth is the CPU core. You have two hands and one mouth. Non hyperthreading is eating with one hand. Hyperthreading is like eating with two hands.
Heh. Something like that, but that's oversimplified. You've got to consider how fast your servers can replace the food, how much your digestive system can process, etc.

---

### Post by weatherman2 on 2014-12-18
> **p2ranger said:**
> Thanks for the input.

The i5's do not have hyperthreading.

Every i3 and i5 I've seen has hyperthreading.  Which i5 did you see advertised without hyperthreading?

Your 330 has hyperthreading, too, actually.  Some budget Intel CPUs do not.

---

### Post by Yellow Pasque on 2014-12-18
> **weatherman2 said:**
> Every i3 and i5 I've seen has hyperthreading.

Citation? Please tell me which CPU's on this list have HT. [http://ark.intel.com/products/family/75024/4th-Generation-Intel-Core-i5-Processors#@Desktop](http://ark.intel.com/products/family/75024/4th-Generation-Intel-Core-i5-Processors#@Desktop)

---

### Post by ibjsb4 on 2014-12-18
What about Xeon?  Been running them for years, find them to be linux friendly and a lot of bang for the buck.

---

### Post by weatherman2 on 2014-12-18
> **Temüjin said:**
> Citation? Please tell me which CPU's on this list have HT. [http://ark.intel.com/products/family/75024/4th-Generation-Intel-Core-i5-Processors#@Desktop](http://ark.intel.com/products/family/75024/4th-Generation-Intel-Core-i5-Processors#@Desktop)

It appears Intel has upgraded many of the i5s to replace hyperthreading with real cores in the recent generations - so instead of two real cores with hyperthreading you'd have four real cores without - certainly faster.  Sorry, I wasn't aware of that.  
 
This slower i5 4th gen still has only two cores with hyperthreading instead of four cores without:

[http://ark.intel.com/products/78929/Intel-Core-i5-4210H-Processor-3M-Cache-up-to-3_50-GHz](http://ark.intel.com/products/78929/Intel-Core-i5-4210H-Processor-3M-Cache-up-to-3_50-GHz)

Instead of asking, "Do I need hyperthreading?" maybe you should ask how much performance you really need?  As I said, hyperthreading simply gives one core two logical CPUs (to the operating system) and is like having maybe half an extra core (approximately).  You can assume an i5 with two cores and hyperthreading will be slower than an i5 with four cores/no hyperthreading...or an i7 with six cores and hyperthreading would be even faster.

---

### Post by pqwoerituytrueiwoq on 2014-12-19
> **ibjsb4 said:**
> What about Xeon?  Been running them for years, find them to be linux friendly and a lot of bang for the buck.+1
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819117316](http://www.newegg.com/Product/Product.aspx?Item=N82E16819117316) 253$ w/ hyperthreading
* not all xeon CPUs have a integrated GPU
a gpu is not required to boot a server is it?

---

### Post by p2ranger on 2014-12-20
Thanks for the input

I'm glad Xeon was thrown out there. I had dismissed it at some point because I thought it would be more expensive overall, but I wound up going with one. Here's what I got ([http://pcpartpicker.com/p/XJ8Jqs](http://pcpartpicker.com/p/XJ8Jqs)):


[LIST]
[*]CPU - Intel Xeon E3-1246 V3  (3.5GHz Quad-Core Processor)
[*]MB - ASRock H97 PRO4 ATX
[*]Memory - Crucial Ballistix Tactical 16 GB DDR 1600 Memory
[*]HD - WD Red 4 TB HD (two), WD Blue 1 TB 7200 RPM
[*]Case - Inwin PE689 ATX Mid Tower
[*]PSU - Corsair CSM 450W 80+ Gold
[*]Fan - Cooler Master 120 mm
[/LIST]

---

### Post by pqwoerituytrueiwoq on 2014-12-21
looks good to me, you may want to know about a few newegg combos (may or may not be of interest to you)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2062010](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2062010)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060362](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060362)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060543](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060543)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060544](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060544)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060545](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060545)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060546](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060546)

i was at Best Buy Friday and saw a 1TB WD Blue for 49.99+tax (same price as newegg during black friday sales)

---

