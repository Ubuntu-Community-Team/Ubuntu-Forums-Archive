---
title: "Understanding FSB and Mem clock"
date: 2009-12-02
forum: Hardware
---

### Post by AlexZaim on 2009-12-02
Hello, i want to understand some numbers related to my fsb and memory's speed.

First of all, my bios indicates that i have a cpu speed of 200MHZ with a x11 multiplier (wich makes 2.2 GHz). That's ok. But the strange thing is that ,for memory, it indicates 667 Mhz speed. This confuses me because i get 333Mhz when run the comand:
> 
$ sudo lshw -C memory
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: V1.7 (05/16/2007)
       size: 64KiB
       capacity: 448KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: pipeline-burst internal varies data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: pipeline-burst internal varies unified
  *-memory:0
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 1GiB
     *-bank:0
          description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
          product: PartNum0
          vendor: Manufacturer0
          physical id: 0
          serial: SerNum0
          slot: DIMM0
          size: 1GiB
          width: 64 bits
          clock: 333MHz (3.0ns)
     *-bank:1
          description: DIMM [empty]
          product: PartNum1
          vendor: Manufacturer1
          physical id: 1
          serial: SerNum1
          slot: DIMM1
  *-memory:1 UNCLAIMED
       description: Memory controller
       product: CK804 Memory Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:00.0
       version: a4
       width: 32 bits
       clock: 66MHz (15.2ns)
       capabilities: ht bus_master cap_list
       configuration: latency=0



From this post, it is obvious that i mean cpu speed= fsb speed. But things are not that way, or are they? if cpu!=fsb, then how can i know my fsb speed?

---

### Post by cascade9 on 2009-12-02
> **AlexZaim said:**
> First of all, my bios indicates that i have a cpu speed of 200MHZ with a x11 multiplier (wich makes 2.2 GHz). That's ok. But the strange thing is that ,for memory, it indicates 667 Mhz speed. This confuses me because i get 333Mhz when run the comand:

333Mhz, but its 'double data rate' so some places have 667Mhz. DDR moves x2 as much data per clock cycle, which is the justification for the 200/400, 333/667, 400/800, blah blah difference. 

As for why you FSB and memory speeds are not in synch, thats something thats been possible for a long time. IIRC, the 1st time you could do it was around the celeron 'a' days (celeron 300). In your case, if you ran the RAM @ the 200mhz FSB speed, you would running aprox. 60% less bandwidth to your memory. Its a good thing you dont have to lock the RAM speed to the FSB, thats a noticable drop.

---

### Post by AlexZaim on 2009-12-02
Then it means that for better performance i have to upgrade my cpu (mainly fsb) and not my ram?
Higher ram clock will get me nowhere with the same cpu,right?

---

### Post by cascade9 on 2009-12-03
Yes, higher clock speed RAM wont help much. Maybe 5-10%, at best, in the real world.

But upgrading your CPU is more about the actually CPU (cache and core speed), not the FSB. 

Eg- IF you had a C2D 6300 (1867Mhz, 2MB cache, 1066FSB) you could upgrade to a C2D T9300 (2500Mhz, 6MB cache, 800FSB).  That would be a major performance upgrade, but the FSB is lower.

---

### Post by AlexZaim on 2009-12-03
My motherboard specifications say that it supoprts 1000Mhz fsb. Does that mean that if i buy a proccessor with 2000Mhz FSB, it will run only at 1000Mhz fsb? 

[The proccessor ]("http://wheretobuy.amd.com/us-en/prodinfo/1012825.html?info_tab")

By the way, if the FSB is just for realising the connection between the CPU and RAM then how come many of them have higher speed than the RAM itself :/ ?
===
Edit:
And how come a single core(1.8ghz) with lower speed and less fsb speed(1 ghz) is more expensive than a dual core(3ghz each) with fsb 2Ghz ?
Compare
[This]("http://wheretobuy.amd.com/us-en/prodinfo/1012982.html?info_tab")
with 
[This]("http://wheretobuy.amd.com/us-en/prodinfo/1012825.html?info_tab")

---

### Post by cascade9 on 2009-12-03
Ahh, its an AMD. To be honest, I'm a bit confused, the 6000+ is meant to run at 3.0Ghz- 200Mhz x 15. 

That 'bus speed' isnt the FSB, its HyperTransport, which replaces FSB on 64bit AMDs. The '200Mhz' is pretty much the old FSB, while HyperTransport is a lot more complicated. Its not just a CPU<-> RAM connection, it also does a lot of point to point connections (northbridge to southbridge, CPU to PCI-E, etc) 

But, yes, if you buy a CPU that has 2Ghz HyperTransport, and your motherboard only supports 1Ghz then your limited to 1Ghz. I'd be interested to know what motherboard your running, 

As for your comparison, the +6000 is a desktop level CPU, the Opteron is a server level CPU. Compare the costs of a core 2 duo (desktop) with a intel xeon (server), you'll see the same thing. 

BTW- I assumed that you were running an Intel CPU. They dont respond as well to faster RAM as the AMDs do. You might get a bit more out of faster RAM on an AMD system. If your board supports DDR2 1066 then it might be worth upgrading your RAM. You still wont see as much increase as if you got a faster CPU, but there might well be more like 10-20% increase, or possible even higher. Depending on what task your doing ;)

---

### Post by rachael4u on 2009-12-03
thnxxxx for the info...

---

### Post by AlexZaim on 2009-12-04
> Ahh, its an AMD. To be honest, I'm a bit confused, the 6000+ is meant to run at 3.0Ghz- 200Mhz x 15. 

I'm confused of your confusion. :) What do you mean it's 'meant'? What's so strange about it.

And what do you mean that > The '200Mhz' is pretty much the old FSB

From what i know, is that amd cpu have their memory controller in the cpu itself, while intel uses fsb's memory controller. I also know that HT technology is a 'tunnel' oriented one. It has tunnels in a daisy chain structure. (see picture)

What's so different from a desktop and a server? They can have the same motherboards don't they? How come some cpu's are for servers other are for desktops... It's the first time i hear that they are distinct from each other by hardware. I thought they differ just from the purposed functionality .

My mother board is MSI k9n4 Ultra, it supports up to 800Mhz DDR2,btw.

---

### Post by cascade9 on 2009-12-04
> **AlexZaim said:**
> I'm confused of your confusion. :) What do you mean it's 'meant'? What's so strange about it. 

Its strange because "200MHZ with a x11 multiplier" doesnt mesh with 200 x 15. Its its downclocked because of low CPU requirements, I thought that it dropped to 800Mhz. Never checked that myself LOL. 

> **AlexZaim said:**
> 
And what do you mean that 

From what i know, is that amd cpu have their memory controller in the cpu itself, while intel uses fsb's memory controller. I also know that HT technology is a 'tunnel' oriented one. It has tunnels in a daisy chain structure. (see picture) 

Yeah, HyperTransport is tunneling. By 'its the old FSB' I mean that 'you access you memory at xxx rate'. There is no FSB on current AMDs. 

> **AlexZaim said:**
> What's so different from a desktop and a server? They can have the same motherboards don't they? How come some cpu's are for servers other are for desktops... It's the first time i hear that they are distinct from each other by hardware. I thought they differ just from the purposed functionality .

My mother board is MSI k9n4 Ultra, it supports up to 800Mhz DDR2,btw.

Whats so different? Well, apart from 'real' servers running EEC, buffered or registered RAM, which I've never seen on a desktop, they tend to have different CPU sockets. Opterons did have socket 939 versions, but from what I remember, 939 was in a grey area. There was desktop 939s, with standard RAM, there was also server 939s, with EEC, buffered or registered RAM.

Currently, the opterons are on 'Socket F' (AKA socket 1207). There were also socket 940 versions, and neither of them are desktop CPU sockets.

Also, opterons have lot of versions. The 939 versions of the opteron are all 1xx, with the '1' meaning 'uniprocessor'. You cannot run multipule CPUs on 1xx opterons, for that you need 2xx (dual CPU) or 8xx (4 to 8 CPUs). You needed socket 940 to run the 2xx or 8xx versions. Same goes with the AM2/AM2+/AM3 opterons, except theres an extra digit. 1xxx opterons are uni, 2xxx are dual, 8xxx opterons are 4-8, and the AM2 etc. versions are all 1xxx. To run 2xxx or 8xxx you need socket F. 

Not trying to be all leet about it, but just because you can use a desktop motherboard and CPU in a 'server' doesnt make them like the 'servers' that people pay big money for. Your not going to see a motherboard like this is a desktop anytime soon- 

[http://www.tyan.com/product_board_detail.aspx?pid=637](http://www.tyan.com/product_board_detail.aspx?pid=637)

4x CPU sockets, taking up to 6 core CPUs in each socket, 24 RAM slots, etc. Nasty. :D 

BTW, I was interested to find out what motherboard it was because some of the manufacturers have been know to play with the HyperTransport numbers. Its an nForce 4 so its 1Ghz HyperTransport.

---

### Post by AlexZaim on 2009-12-04
> Its strange because "200MHZ with a x11 multiplier" doesnt mesh with 200 x 15. Its its downclocked because of low CPU requirements, I thought that it dropped to 800Mhz. Never checked that myself LOL.
I'm sorry, what doesn't mesh? Or why should it mesh? I don't see why you suppose it's downclock. Those are two different cpu's :) fist is mine , and the second is the one from AMD's shop... i'm not quite understanding you on that sentance.

But thanx so far! You've helped on this thread.

---

### Post by cascade9 on 2009-12-04
Sorry, about that, I saw this and assumed that you had a +6000- 

> **AlexZaim said:**
> My motherboard specifications say that it supoprts 1000Mhz fsb. Does that mean that if i buy a proccessor with 2000Mhz FSB, it will run only at 1000Mhz fsb? 

[The proccessor ]("http://wheretobuy.amd.com/us-en/prodinfo/1012825.html?info_tab")


My bad....I really should try to sleep more. Maybe if I'm lucky I will tonight. I also should try to use clearer english, I sometimes forget that as a native english speaker I can use terms that can sometimes confuse people who have english as a 2nd language. 

Gald I've been able to help ;)

---

