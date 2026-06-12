---
title: "Tiny linux server with giga LAN"
date: 2018-01-20
forum: Hardware
---

### Post by cazz on 2018-01-20
Hi
I have build a script that run a speed test between two computers.
Now I have done so it go to a server and everything works greate.

The only problem is that the other side I have to use a old HP laptop and it feel to big to use there I want to make a speed test.
So right now I use HP laptop to a server but I like to change the laptop to something else.

I did try with Banana Pi that have 10/100/1000 but when I compare the result from Banana Pi and the Laptop I can see better result on the laptop.
Maybe because it use a SD card and the laptop have a SSD?
Not sure how to fix that, is that any cheap linux computer that I can use that have 1000 LAN

---

### Post by TheFu on 2018-01-20
**iperf3** is the normal method used to test bandwidth between 2 systems.  Using your own script, provided it does exactly what you intend to transfer is a good idea too, but it probably tests the CPU, bus, storage, and all the networking.  iperf3 would test only the network.

Whenever looking for performance slowdowns, you should look at every single component used in the testing.
* hdd
* storage cables
* storage controller
* bus
* CPU
* network drivers/card
* ethernet / wifi connections
* router / access point
* other networking things - firewalls, routers, switches
* and everything just like above on the other side (compute, networking, etc)

Narrow down where the slowdown is, then see what can be done to remove/improve it.

In the old days, not all GigE NICs provided GigE speeds.  That has mostly changed for normal computers, but SBC (single-board-computers) are still limited by their internal bus architectures almost always. I don't know anything about BananaPi, but RaspberryPi systems share a single USB bus for all components. That means at most, 480Mbps is possible, but that is shared between the NIC, storage and any external connected devices.  Plus there is loss when a bus is shared since a traffic cop has to step in to prevent only 1 device from using all the bandwidth. Something similar applies to CPUs, motherboards, addon cards, etc.  Many motherboard makers have systems architecture diagrams which show how things are connected internally.  

For example, I discovered that my USB3 addon card for an older computer was connected to a slower bus that was shared with all the HDD controllers on the system. Basically, that bus was already flooded with SATA transfers from internal and external disks, so the USB3 connected storage never got anywhere near the bandwidth advertised.  Short of buying a new motherboard (which also means a new CPU + new RAM), there isn't a solution on that equipment.

So, simplify your test setup to move components from the test direction you are going. If you only want to test bandwidth between 2 systems, then don't test storage systems.  For storage testing, use **bonnie++** and don't test network stuff.

Of course, after you've gotten all the parts figured out for where the slowdowns are happening, when all those components are put back together into a file transfer test, that is really what matters. And good job using a script to perform the initial testing to determine there actually is some issue to be resolved or at least understood.

Comparing SSD to SDHC performance doesn't make sense.  That's like comparing a $500,000 sports car to a $2,000 used pinto.

As for a cheap computer that provides fast server capability, it really depends on the purpose of the server.  For many homes, a banana pi or raspberryPi would be overkill for running a nextcloud + email + calendar + contacts + home chat server.  OTOH, if you want a backup server, then network and storage performance would be key. For that, I think about $75 for a used desktop would be the starting point or $130 for a new computer build leveraging old components for everything except the MB, CPU, and perhaps RAM.

There are lots and lots of options, but the lower end stuff is extremely localized - completely depends on your part of the world. As an example, there are mom-n-pop computer stores where I live that have used computers cheap.  Or I could visit the local microcenter (about 8 miles away which sells off-lease computers for $75-$150).  OTOH, I have a few of those cheap systems here that are semi-retired and I'm looking to spend about $400 on a Ryzen 5 1600 system (MB+CPU+RAM). Everything else will be reused from other components laying around.  A new computer with that CPU would run $850+ (microcenter is $999).

A big question is how important is physical size for you?  Tiny computers that are fast will cost more than a mid-tower computer.  Really small ARM-based computers won't have sufficient CPU to run Plex Server if any transcoding is needed.  If transcoding isn't needed and only 1 stream needs to be supported, then a r-pi v3 will handle it.
How important is being silent? Battery backup included?  Power use?  Will it be a pure server or will it be a dekstop too?

As you can see, it comes back to the requirements. What do you want?

---

### Post by cazz on 2018-01-20
Thanks for the replay and I think I did write a little wrong (English is not my first language) so I trying to write a little better :)

Right now I have a server that is close the our incoming fiber.
I do use iperf3 in my script and the script is running on a laptop that I take to a place that I want to see how good speed it is between the place and the server.
It works very well and I have made so it send the result to the server that store it in MySQL so it run every 30 min for some days and after that I can read the result.
It make me see if the networks drop and what time so I can see what I can do.
It also good to see what speed they have if they now say they have a very slow speed.
I just like to find some tiny computer that I can replace the laptop, even if the laptop is tiny (13" laptop) it still feel big.


My idea is to make a cheap easy to use networks tools for me and my colleagues, sure I know I can buy some very expensive system to do that but I like to see what I can do alone :)
So on the server side I have nothing to worry about it is the other side the I need to find something to use other then the laptop

The Raspberry Pi 3 does only have 10/100 NIC build inside, it also only have USB 2.0 (480 mbps) so I do not like to use that
The Banana Pi does have 10/100/1000 NIC build inside and that is good but the SDHC is not good.
The SDHC class 10 have a read speed around 90 MB/s when SSD have around 520 MB/s

So I guess I need some tiny computer like Intel NUC or similar with SSD.

---

### Post by TheFu on 2018-01-20
For a small computer, think mini-ITX motherboard, not a NUC, if you care about costs.

NUC is VERY, VERY, expensive.  About $150 over the cost of a shoebox-sized mini-ITX case. [https://www.reddit.com/r/buildapc/comments/53f3wp/dont_buy_a_nuc_build_a_thin_miniitx_system_instead/](https://www.reddit.com/r/buildapc/comments/53f3wp/dont_buy_a_nuc_build_a_thin_miniitx_system_instead/)

Heck, mini-ATX is an option too: [http://www.pcgamer.com/head-2-head-mini-itx-vs-microatx-systems2015/](http://www.pcgamer.com/head-2-head-mini-itx-vs-microatx-systems2015/)  I have a Core i7 from "Shuttle" which is less than half the size of a mid-tower, but has all the power, supports 2 HDDs, optical drive, eSATA and has an nVidia Quadro FX GPU! Lower power versions are available for less.

You can find mini-ITX systems for $100, new, with intel or AMD CPUs.  I have 1 from 2011-ish and it was $99.  An AMD E-350 that used to be a media server, but the onboard-GPU didn't support hidef decoding of h.264 or mpeg2 video, so it was replaced.  

An SSD isn't needed for what you want. Actually, the DBMS isn't needed either. Just writing to a text file (appending) would easily do what you need.  But I suspect this is something you enjoyed creating, plus it enhanced a skill.

Cheap SSDs don't get anywhere near 500 Mbps. Think more like 180 Mbps, but for writing a few records to a DBMS, any SSD is overkill.  Any old HDD (spinning rust) would easily handle anything you have at home. I wouldn't spend $0.01 on new storage, just use an old HDD.

For something better than a r-pi, but less than a $450 NUC, the mini-ITX stuff fits.  There are some Arm systems like an Odroid which can do GigE and have SATA ports (via a special connector), but total systems end up costing $150+ and for that price a mini-ITX with an x64 CPU would be much more compatible.

An odroid build: [https://category5.tv/shows/clips_tech/episode/529-xu4q-cloudshell2/](https://category5.tv/shows/clips_tech/episode/529-xu4q-cloudshell2/) . I haven't heard about drive benchmarks, but they built it with 2 SSDs - which is just crazy - but Kingston is a show sponsor, so perhaps those were free?

It all comes back to requirements.

---

### Post by cazz on 2018-01-20
hmm yes I have to look into that but a NUC (DE3815TYKHE) have a Atom E3815 1,46 Ghz and with 2 GB memory it just cost me around $124
I can build my own with mini-ITX but it going to cost me around same price as the NUC

To make it a good investment I need to make a good tools as possible so if they like the idea I have no problem to buy some and show them.

First I need to use the laptop I have and make it as good as possible with iperf3 and maybe even some other networks tools that is good to use.

---

### Post by TheFu on 2018-01-20
That CPU, E3815, is a dog.  It is half the performance of a 2011 AMD E350 system. For pure network stuff, it might be ok, but you can do so much better on the CPU side.

Be careful with any Atom-based CPUs. There have been some important issues.  Definitely look at a J1900-based system first and be certain to compare performance.  The J1900 is almost 5x faster than that E3815.  Lots of people build a home router around the J1900 CPU.
My current router is an APU2-based system.  $144 (total for SBC, case, PSU) with a amd64 CPU (GX-412TC), support for virtualization, but no GPU. Console only local access, but of you run ssh/x2go on it, then no local access is really needed.  Mine is a router, but others use it for cheap desktops.  10W max power. No fans. 100% silent.  Intel NICs, so almost all the network processing happens in the NIC, not CPU.  AES-ni support in the CPU too. The APU2 is just on the lower-edge of performance for a comfortable, non-gaming, computer.  Good for office-productivity and running lite servers, like you plan.  It was overkill for my edge router needs, but I planned to have it for at least a decade, so $10/yr seems pretty reasonable.  I've had it 2+ yrs now running pfsense.

OTOH, only you know how important physical size and performance really are.  Hopefully some others have been reading and will share their ideas.  I certainly don't have the best answer for your needs, but I have been burned a few times making bad decisions which didn't seem that way originally.  Had an early NUC - an i5 miniPC that had overheating issues. There wasn't any upgrade solution, since everything is included. It burned out the motherboard and effectively bricked everything.

---

### Post by cazz on 2018-01-20
mm yes I do not like the Atom, did have one before and it was very very slow. The only positive it was cheap and did not take so much power and was tiny.

---

### Post by mastablasta on 2018-01-22
there is a dedicated group on G+ that deals and discusses only about mini pcs: Mini PCs & TV Boxes

i am sure there are others as well as websites. i was surprised to see how much choice there actually is available. from low powered celerons to powerfull pcs in small boxes.

there are also some good advices on Kodi forums or openelec forums. it is surprising to see how good ratings some noname chinese brands would get. 

in any case i think those that use many and assembled plenty of MiniPCs might have a better advice on what to use.

---

### Post by cazz on 2018-01-22
mm yes but with a little help from here I have some good idea what to buy :)

---

### Post by 1clue on 2018-01-22
Several points.

[LIST=1]
[*]You need to check cables too.
[LIST=1]
[*]Cat5e is the minimum ethernet capable of gigabit transfers.  Yes it matters.  So you need cat5e or cat6. 
[*]One wire can be broken on an ethernet cable and you'll get 100 mbps one direction and gigabit in the other. 
[*]Insulators can be pinched, the cable has a kink in it or any number of other things and you'll get sporadic failures. 
[/LIST]
  
[*]Brand of NIC matters. I have experience with speed testing on two gigabit adapters:
[LIST=1]
[*]Intel I210/I350/I354 which are the same basic thing with different numbers of ethernet ports. They use the 'igb' driver. This NIC handles almost all network processing on the NIC, does DMA to the main RAM and notifies the CPU when finished. 
[*]Realtek RTL8111. Both an on-board NIC and a 4-port PCI card. This NIC handles a few things on the NIC and then interrupts the CPU for heavy lifting. 
[/LIST]
  
[*]Not all Atom boards are the same. The desktop/laptop chips are pretty slow, but the communications or server-based systems are very fast. 
[/LIST]
 

I have an atom c2758 board with 16GiB RAM and 8 cores. [http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm](http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm) It has 7x Intel NICs using the igb driver. This is a communications server platform, not something for your Mom to surf the web. It has built-in SATA3 ports, one of which has an SSD in it.

I have an i7 920 with 24GiB RAM and 4 'real' cores with hyperthreading. Looks like 8 cores to Linux. [https://www.asus.com/us/Motherboards/P6T/](https://www.asus.com/us/Motherboards/P6T/) It has 1x on-board Realtek NIC and a 4-way Realtek PCIe card. It has a SATA3 controller in a PCIe slot, which has an SSD in it.

I did the i7 setup first. Someone mentioned that the Realtek and other low-quality NICs offload much of the processing to the CPU, and you can see it by watching CPU load and interrupt levels. So I did a test between my two boards listed above. Saturating a single NIC on each board, they both get very close to wire speed in both directions. Looking at the CPU usage, the atom board is almost completely idle and the i7 board jumps up to around 20%. Getting more NICs involved shows more of the same.

The i7 beats the atom hands-down on things like compiling.

The atom beats the i7 on encryption, compression and net-to-disk access. These systems both have the same brand of SSD, same generation.

Caveats: Both atom generations (c2000 and c3000) are vulnerable to Spectre/Meltdown. So is my i7. As well, the C2000 has a known hardware bug which permanently bricks the device if your setup is under heavy load for years. There is no workaround. But this 'heavy load' is the sort of scenario you would see with an enterprise network management device, not home use.

If I were setting up something else right now, I'd look at a 2-core Atom c3000 series board with at least one built-in Intel NIC [https://www.supermicro.com/products/motherboard/ATOM/](https://www.supermicro.com/products/motherboard/ATOM/) . As an alternative you might look at netgate [https://store.netgate.com/Single-Board-Computers-C3.aspx](https://store.netgate.com/Single-Board-Computers-C3.aspx) and pay attention to specs. They sell both new and old tech.

There is a ton of hardware out there which is minimalist but designed to handle very high performance networking. It's not as cheap as DIY experimenter boards like Banana Pi or Raspberry Pi. On the other hand it's designed to be put into service and run for years under load without half-assed hardware.

***Edit:** I went through much of your logic a few years ago. Clearly I chose a more expensive route. My atom board cost, all-in, about USD $1,100.00. I do not even slightly regret it. Supermicro does not make junk. At all. That said I also use Raspberry Pi in some situations where reliability does not take down my network. I just don't expect much from them.*

---

