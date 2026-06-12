---
title: "Hardware advice: Building a new server"
date: 2014-03-28
forum: Hardware
---

### Post by sgofferj on 2014-03-28
Hi,

as written elsewhere, my home server is way overdue for a remodel. For a change, I was thinking of going Ubuntu (instead of Opensuse) and I am planning to stuff various services in vboxes for easier maintenance.
Currently, I'm running this services:
[LIST]
[*]Perimeter firewall - that is already in a VM with a dedicated NIC and works fine there 
[*]Storage - NFS and SMB (for DLNA) 
[*]Postfix / Cyrus 
[*]Webserver with currently 7 virtual hosts 
[*]Rendering - I run a weather website at saakeskus.fi and every 6 hours, the server pulls about half a gig of raw data, renders some 6500 charts and uploads them to my webhoster 
[*]Asterisk PBX (all network, no PCI cards) 
[*]DLNA server (Mediatomb) 
[*]Home automation, control and security - a whole collection of stuff knitted together with scripts 
[*]And a whole bunch of small stuff, like monitoring and so on 
[/LIST]

The current box is an AMD Phenom 8650 with 6GB RAM. A year ago, my RAID failed - both disks burned out within days from each other... So I had to invest quite a bit of money for the Seagate Recovery service. NOT NICE! At the moment, I'm running on the USB disk they sent me with my rescued data.
Anyways, one of the major issues I have, besides that server just being old and becoming unreliable, is power consumption. The 8650 has 95W TDP on the paper but the whole system almost suck me dry. I have over 500kWh per months and one of the criteria for the new server definitely is "POWER SAVE"! The other thing is that it's a HOME server, so I can't have a screaming DELL/HP/IBM/whatever pizzabox which produces more dB than a Hornet on afterburner.

I'm totally no hardware guy, so I'd be grateful for some ideas on where to start with building the new machine.

Edit: Forgot - of course, mysql also runs on that machine with several dbs.

---

### Post by castlefox on 2014-03-28
How did your old hardware of  AMD Phenom 8650 with 6GB RAM deal with the needs listed already?   IE do you need more horsepower to do what you want to do or no?

Just wondering how much storage you are going to put in this?

What kind of budget do you have?

---

### Post by sgofferj on 2014-03-28
Budget is "as much as needed", excluding waste such as buying some brandname datacenter machine for $7k or so.
Horsepower-wise, the box is idling around 10% most of the time. During chart rendering it goes up to about 40%. A little bit more would still be nice because at the moment, I limit the rendering to 1 core to protect the other services and thus it takes over an hour.
Storage-wise, I was thinking of something like 4x2, 4x3 or 4x4 TB on ZFS or BTRFS.

---

### Post by Yellow Pasque on 2014-03-29
1. For processor, AMD offers better value for parallel tasks (IMHO) because Intel considers Hyperthreading a premium feature. You may want to look at the Kaveri chips:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819113360](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113360)
If considering intel, I would be looking at i7-4770s because they're quad-core with Hyperthreading and Vt-d support. Just make sure to avoid the 4770K or any K-series chip because they're for overclockerz/gamerz.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116902](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116902)

2. Carefully research your mobo's IOMMU (AMD-Vi/Intel Vt-d) implementation because I see a lot of complaints about faulty implementations (my current mobo also suffers this issue).

3. RAM's relatively cheap, so load up. (I don't normally advise people to do that, but your usage case is one that could actually benefit from a ton of RAM.)

---

### Post by leonmaxx on 2014-03-29
I'd recommend an AMD FX-8320 + ASUS Sabertooth 990FX mainboard. FX-8320 is cheapest 8-core CPU on the market and is still very powerful, the mobo i recommended have extended lifetime (due to component quality) and 5 years warranty. These CPU and mobo combination have working AMD-Vi support. Xen and KVM works without problems, and You'd better use KVM instead of vboxes, KVM virtual machines is far more faster.

Sorry for my bad English.

---

### Post by sgofferj on 2014-03-29
The FX-8320 has a TDP of 125W, so I would massively increase my electricity bill... AMD-wise, I was looking at an A10-6700 which has 65W TDP including a graphics core, but I'm not sure how good the virtualization support is.

@Temüjin:
Thx. I was planning for maybe 16, maybe 32G ECC.
But exactly that CPU/MB issue made me post here. Hardware is such a fast-changing topic - if you turn away for a moment, you're out and I haven't looked at hardware in years as it was never my topic.

---

### Post by leonmaxx on 2014-03-29
> **sgofferj said:**
> The FX-8320 has a TDP of 125W, so I would massively increase my electricity bill... AMD-wise, I was looking at an A10-6700 which has 65W TDP including a graphics core, but I'm not sure how good the virtualization support is.

Ok, then there is FX-6300 with 95W TDP (same as Your old Phenom) 6-cores is still better for server than 4-cores of APU You suggested. And why do You need graphics core on a server?

If You still want A10-6700 - yes, it supports virtualization, and I can recommend You a motherboard with working AMD-Vi: ASUS A88XM-A.

---

### Post by QIII on 2014-03-29
Hello!

The difference between the FX and the A10 in terms of wattage is 125W - 65W = 60W.  I don't think running an extra 60W lightbulb in your house would cause a "massive" increase in your electricity bill.

I'd make the decision based on cost of components and what you plan to have your server doing.  You might not need a powerful processor.  There's a cost difference between the FX and the A10.  Also, the HSF for each is going to have to be suitable.  An HSF capable of cooling the FX is going to be more expensive than one to cool the A10.  In fact, the OEM cooler may be sufficient for the A10 if it doesn't ever get taxed.

I guess what I am saying is that energy consumption is really just so much FUD.  In a year's time, the cost of the extra electricity will be much less than the initial purchase of the components.  So make a wise decision on those expenditures based on what you need your machine to do.

Cheers!

---

### Post by sgofferj on 2014-03-29
Well...

Here in Finland electricity is quite cheap, compared to the rest of Europe but here's a little calculation:
Electricity costs: 0,0696&#8364;/kWh
Transport costs: 0,038&#8364;/kWh (that's what the local electricity company gets for using their cables)
Energy tax: 0,0235972/kWh
Total: 0,1311972&#8364;/kWh

60W running 24/7 (it's a server, after all) make
0,188923968&#8364; (1,44kWh)/day
5,66771904&#8364; (43,2kWh)/month
68,95724832&#8364; (525,5kWh)/year

That's roughly 10% of my total consumption of roughly 5500kWh last year!
And 69&#8364;/year is a pretty good starting point for an amortization calculation when looking at the price difference between power-saving and power-wasting hardware.

And... that's just the CPU... I haven't even started to take other components into account, such as the graphics chip which is integrated and therefore included in the TDP of the A10 Core i7 or other components.

Edit: as I wrote, my current machine is most of the time idling around 10%, so I don't really see the need for some 8 core "monster" CPU :)

---

### Post by QIII on 2014-03-29
> **sgofferj said:**
> 
Edit: as I wrote, my current machine is most of the time idling around 10%, so I don't really see the need for some 8 core "monster" CPU :)

Well, that's another consideration.  We were calculating on full throttle.  The difference in power consumption drops significantly when considering that.

The decision most certainly becomes less a matter of electricity bill and more of initial cost of components.

A server doesn't necessarily have to rumble like a locomotive when a moped will do.   Regardless of the fuel consumption, the moped is cheaper.

EDIT:  By the way, my 60W bulb burning 24/7 costs me $36.76US annually -- and that's actually running at 60W.  At 10%, that goes down to $3.68.

---

### Post by sgofferj on 2014-03-29
> **QIII said:**
> Well, that's another consideration.  We were calculating on full throttle.  The difference in power consumption drops significantly when considering that.
Of course, but a generally more powersaving system also is more powersaving on just idle, i.e. e.g. less heat waste :). And I'd guess, that's especially true with current hw. The Phenom 8650 is what - 4 years old? I actually measured it and the whole system pulls 150W on idle and 170W on 300% (all 3 cores running 100%). The CPU itself has a TDP of 95W...

> The decision most certainly becomes less a matter of electricity bill and more of initial cost of components.
EDIT:  By the way, my 60W bulb burning 24/7 costs me $36.76US annually -- and that's actually running at 60W.  At 10%, that goes down to $3.68.

With your electricity costs, I see your point :). In USD (todays exchange rate), 60W cost me roughly $95/year.

Besides, the AMD FX-8320 costs €137,90 in Europe while the A10-6700 only costs €119, so powersaving is even cheaper :).


@leonmaxx:
Thanks for the info on the board!
I don't "need" a graphics core on a server - it's a matter of calculation. The A10-6700 has 65W TDP including graphics chipset (which I actually can use for rendering also with OpenCL). If I'd take a CPU without display chipset included, the display chipset would be on the MB, so it would be "extra" power consumption in the whole calculation.

Anyways, I'm not nailed down to AMD... While researching in the web, I found some Intel chips which are supposed to have only 35W TDP? Core i3...? What's the thing with them?

---

### Post by sgofferj on 2014-03-29
> **leonmaxx said:**
> If You still want A10-6700 - yes, it supports virtualization, and I can recommend You a motherboard with working AMD-Vi: ASUS A88XM-A.
Do I see right that that board does NOT support ECC RAM? I know, I forgot to write this earlier, but I'd like to use ECC. My current server used to have 8GB RAM and just a few weeks ago I started getting weird segfaults and stuff. After hours of debugging, I ran memtest and found that the upmost 2GB bar had some faulty cells... With ECC I'd probably have noticed that much faster as my Linux kernel would have screamed at me about it...

---

### Post by leonmaxx on 2014-03-29
> **sgofferj said:**
> Do I see right that that board does NOT support ECC RAM? I know, I forgot to write this earlier, but I'd like to use ECC. My current server used to have 8GB RAM and just a few weeks ago I started getting weird segfaults and stuff. After hours of debugging, I ran memtest and found that the upmost 2GB bar had some faulty cells... With ECC I'd probably have noticed that much faster as my Linux kernel would have screamed at me about it...

Looks like ECC RAM is not supported by APUs at all.

[QUOTE=sgofferj]I found some Intel chips which are supposed to have only 35W TDP? Core i3...? What's the thing with them?[/QUOTE]

First take a look if it supports VT-x and VT-d, Intel is known to be greedy on VT-d in cheap CPUs.

---

### Post by Yellow Pasque on 2014-03-29
> **sgofferj said:**
> While researching in the web, I found some Intel chips which are supposed to have only 35W TDP? Core i3...? What's the thing with them?

The thing? They're just like regular Core i3's, except they showed excellent electrical characteristics in testing, so Intel "binned" them separately and charges a bit more for them. Core i3's don't support Vt-d though...

The Core i5-4440S might be worth a look: [http://ark.intel.com/products/75040/Intel-Core-i5-4440S-Processor-6M-Cache-up-to-3_30-GHz](http://ark.intel.com/products/75040/Intel-Core-i5-4440S-Processor-6M-Cache-up-to-3_30-GHz)

---

### Post by sgofferj on 2014-03-29
"Regular Core i3"... :D I think you underestimate how clueless I am when it comes to hardware :D.
Hm, basically, I'm back to where I was now... Too many options and too little current knowledge to make a decision...

Let me summarize again... I wanna remodel my homeserver which runs 24/7. Electricity is expensive here in Finland (at least much more expensive than in the US) and it's likely gonna get even more expensive soon thanks to energy taxes, so power consumption is a big issue. Otherwise I need virtualization support, min. 6xSATA (system disk, 4x storage, hot spare), support for ECC RAM. I do *not* need excessive computing performance - performance-wise even my current old Phenom 8650 is mostly sufficient. My budget is "as much as needed", means, I don't care if a CPU cost $100 more than another one if it can save 50 or 60W because I will have the price difference amortized within a year. And of course, it should run under Ubuntu Server :).

---

### Post by Yellow Pasque on 2014-03-29
> **sgofferj said:**
> "Regular Core i3"... :D I think you underestimate how clueless I am when it comes to hardware :D.
It's just a model name. Don't freak out about it... Just look for the features you want. If power is really, really important to you, then the choice is fairly easy in my opinion (at least on Intel side).
**Core i5 4670T** - 45W, 2.3GHz quad core, Vt-d, HD4600 graphics

---

### Post by sgofferj on 2014-03-29
> **Temüjin said:**
> If power is really, really important to you, then the choice is fairly easy in my opinion (at least on Intel side).
**Core i5 4670T** - 45W, 2.3GHz quad core, Vt-d, HD4600 graphics
What would be a suitable board? I have been checking S1150 boards from Asus at alternate.de but the ones I find interesting (mostly P9D variants with 2x or 4xNIC or others which support ECC RAM) don't seem to support Core i5... E.g. P9D-C/4L says supports Intel® Core™ i3 (Haswell), Intel® Pentium G (Haswell), Intel® Xeon E3 v3 (Haswell), but nothing about Core i5...

---

### Post by Yellow Pasque on 2014-03-29
> says supports Intel® Core&#8482; i3 (Haswell), Intel® Pentium G (Haswell), Intel® Xeon E3 v3 (Haswell), but nothing about Core i5... 
See list here: [http://www.asus.com/us/Commercial_Servers_Workstations/P9DC4L/#support](http://www.asus.com/us/Commercial_Servers_Workstations/P9DC4L/#support)
It doesn't support i5, nor does it support integrated graphics. That board is meant to be used headless, so if you don't mind that, then the CPU that you would probably like is the **Xeon E3-1230L v3**, quad core with Hyperthreading, 1.8GHz (2.8GHz Turbo) , no integrated graphics, 25W TDP: [http://ark.intel.com/products/75053](http://ark.intel.com/products/75053)

---

### Post by sgofferj on 2014-03-29
I think you misunderstood me :). I meant, which would be a suitable board for the Core i5 you suggested? That P9D was just an example for all the boards in the list which don't seem to support Core i5.
The board does have some primitive graphocs chip onboard and a VGA out :). Plus a "management LAN" - I suppose that is some KVM over ethernet stuff, ideally VNC or RDP?
I'm not so familiar with Xeon but 1.8GHz sounds a bit too slow. That would be slower than my current Phenom, although 25W TDP sound pretty awesome!

---

### Post by Yellow Pasque on 2014-03-29
> I meant, which would be a suitable board for the Core i5 you suggested?
I personally don't know in this case. If you intend to use ECC RAM and make heavy use of IOMMU, make sure you do your research/homework. Maybe someone else can give you more specific suggestions..

> I'm not so familiar with Xeon but 1.8GHz sounds a bit too slow
If you do put the chip under really demanding load, it will Turbo Boost to 2.8GHz. Actually, it sounds ideal for your workload.
> That would be slower than my current Phenom
You can't make a direct comparison just looking at clock speed (for example, a 3.0GHz Phenom is way faster that a 3.4GHz Pentium 4).

---

### Post by sgofferj on 2014-03-29
Ok... that sounds pretty good :). Is this turbo boost configurable or does the cpu decide it all by itself?
I'll try to google some benchmarks.

---

### Post by sgofferj on 2014-03-29
Well, that's why I didn't find it at Alternate... It's not available :(.
[http://reviewbros.com/2013/10/07/intel-cpu/](http://reviewbros.com/2013/10/07/intel-cpu/)

Edit: you were right. Passmark says 2031 for my Phenom 8650 an 7344 for the E3-1230lv3.

---

### Post by Yellow Pasque on 2014-03-29
> **sgofferj said:**
> Is this turbo boost configurable or does the cpu decide it all by itself?

The CPU does it: [https://en.wikipedia.org/wiki/Intel_Turbo_Boost](https://en.wikipedia.org/wiki/Intel_Turbo_Boost)

The Xeon E3-1230L is a 6/7/9/10 turbo scheme, so if you had all four cores loaded, it would run at 2.4GHz, three cores would be 2.5 GHz, two cores would be 2.7Ghz, and one core is the full 2.8Ghz.

Does your weather processing scale well with more cores/threads? (i.e. is it a parallel problem)?

---

### Post by Yellow Pasque on 2014-03-29
That doesn't surprise me. Those chips are incredibly efficient, so of course they go to OEM's :(

---

### Post by sgofferj on 2014-03-29
> **Temüjin said:**
> Does your weather processing scale well with more cores/threads? (i.e. is it a parallel problem)?
The rendering tool doesn't. It doesn't know multithreading. But I have split the load in several jobs which I can simply start in parallel. My system just doesn't have enough cpu and i/o power. If I run more than 1 render job in parallel, the rest of the services break in, especially asterisk and dlna/mediatomb.

---

### Post by lukeiamyourfather on 2014-03-31
I recently ordered one of these to build a file server for a small non-profit organization. It was like $350 from Newegg if I recall.

[http://www.asrockrack.com/general/productdetail.asp?Model=C2750D4I](http://www.asrockrack.com/general/productdetail.asp?Model=C2750D4I)

It has 8 processor cores at 2.4GHz, 20W TDP, up to 64GB of ECC memory, and 12 SATA ports. Also mini ITX form factor! All it's missing is 10GbE and it would be the perfect file server. Though it has a PCI Express slot if you need that too.

---

### Post by Yellow Pasque on 2014-03-31
The Avoton is an Atom-based CPU, so if OP's needs aren't met by a triple core Phenom, I suspect the Avoton would be underpowered too.

---

### Post by lukeiamyourfather on 2014-04-01
> **Temüjin said:**
> The Avoton is an Atom-based CPU, so if OP's needs aren't met by a triple core Phenom, I suspect the Avoton would be underpowered too.

The C2750 is significantly faster than that. Check out the reviews of it and the benchmarks. It's pretty astonishing performance for 20 watt TDP (on par with the Opteron 3380, which is 8 cores at 2.6GHz).

---

### Post by sgofferj on 2014-04-01
That looks like the perfect solution for my Secondary Storage NAS. Maybe a bit too underpowered for the main server as that would have a bit more on it's plate than just file serving.

@Temüjin:
Performance-wise, my Phenom is pretty ok for the task - with careful ressource-management, but my system is just old and getting flaky plus it draws way too much power, hence the rebuild.

---

### Post by sgofferj on 2014-04-03
Well, the 1230L V3 is available in May here. I just have a problem with the board. I was looking at the Asus P9D-M or P9D-C/4L but I couldn't determine with certainty if they support VT-d. The feature list doesn't say anything and also I couldn't find definitive infos about the C224 chipset. However, in the [manual for the P9D-C/4L]("http://dlcdnet.asus.com/pub/ASUS/mb/socket1150/P9D-C/Manual&AVL/e7916_P9D-C_Series_for_web.pdf"), on page 4-17 it says something about enabling VT-d and so does the [manual of the P9D-M]("http://dlcdnet.asus.com/pub/ASUS/mb/socket1150/P9D-M/Manual&AVL/E8096_P9D-M_series_VER8096.pdf") on page 4-18.

[IMG]http://www.cheesebuerger.de/images/more/bigs/c002.gif[/IMG] [IMG]http://www.cheesebuerger.de/images/more/bigs/a136.gif[/IMG]

---

