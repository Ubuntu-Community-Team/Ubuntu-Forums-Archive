---
title: "Ubuntu Machine doesn't recognize RAM - HELP!!!"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by ghostofzuul on 2009-03-30
Hello,

I have an old gateway running 8.04 hardy. It came with 512MB RAM PC133. Here's the relevant part of my lshw:

 *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: DIMM0
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 100MHz (10.0ns)

for some reason when I install additional memory, the machine doesn't recognize it. It doesn't matter what size. 256mb or 512mb. I have a mac that also uses pc133 and memory that the ubuntu machine doesn't recognize is in fact recognized by the mac. It doesn't matter which slot i use on the ubuntu machine so i know both slots are working... just won't recognize the 2nd stick of ram regardless of the slot.

I have this extra PC 133 memory around I'd like to use but none of the extra sticks I have work in the ubuntu machine while they all work in the mac... any ideas? still kinda a newbie at this so any help would be great... thanks!

---

### Post by ghostofzuul on 2009-03-30
> **ghostofzuul said:**
> Hello,

I have an old gateway running 8.04 hardy. It came with 512MB RAM PC133. Here's the relevant part of my lshw:

 *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: DIMM0
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 100MHz (10.0ns)

for some reason when I install additional memory, the machine doesn't recognize it. It doesn't matter what size. 256mb or 512mb. I have a mac that also uses pc133 and memory that the ubuntu machine doesn't recognize is in fact recognized by the mac. It doesn't matter which slot i use on the ubuntu machine so i know both slots are working... just won't recognize the 2nd stick of ram regardless of the slot.

I have this extra PC 133 memory around I'd like to use but none of the extra sticks I have work in the ubuntu machine while they all work in the mac... any ideas? still kinda a newbie at this so any help would be great... thanks!

someone in another pointed out to me that in fact my motherboard might be limited to 512MB of ram... seems like when i use 2 sticks of 256 it works fine... yikes. need a new motherboard? how hard are those to install?

thanks!

---

### Post by infoseeker on 2009-03-30
Some of the older motherboards required 2 sticks of identical RAM modules to work, something about single/double sided RAM ;)

---

### Post by woppy71 on 2009-03-30
> **ghostofzuul said:**
> someone in another pointed out to me that in fact my motherboard might be limited to 512MB of ram... seems like when i use 2 sticks of 256 it works fine... yikes. need a new motherboard? how hard are those to install?

thanks!

Thats unfortunate, but sometimes true... the older pc gear gets, the more difficult it is to get upgrades for it.

Installing a new motherboard can be as easy as you want it to be, providing you assemble everything you need before hand, but seeing as it sounds as though you have quite and old system, a motherboard upgrade may not be viable, it's going to be a lot easier and cheaper in the long run, to buy some new kit, wether that be a part built system (which maybe the way to go, seeing as you would be able to use some of your old hardware, such as the dvd drive, hard disk etc, or you may chose to buy an entry level machine, ready built.

Swings and roundabouts, i'm afraid, but I would highly recommend looking at buying some new kit.

do you perhaps have a friend who has some PC building experience? They could perhaps give you a little support with any potential new build. The trick is not to be scared of building a PC, just take your time and assemble all the tools you need, and you can't go far wrong. Good luck! :grin:

---

### Post by rjl6591 on 2009-03-30
If your BIOS settings have been tweaked to run the RAM as fast as possible, try slowing it down a bit. Sometimes it's necessary to do this when adding extra RAM.

---

### Post by ghostofzuul on 2009-03-30
> **woppy71 said:**
> Thats unfortunate, but sometimes true... the older pc gear gets, the more difficult it is to get upgrades for it.

Installing a new motherboard can be as easy as you want it to be, providing you assemble everything you need before hand, but seeing as it sounds as though you have quite and old system, a motherboard upgrade may not be viable, it's going to be a lot easier and cheaper in the long run, to buy some new kit, wether that be a part built system (which maybe the way to go, seeing as you would be able to use some of your old hardware, such as the dvd drive, hard disk etc, or you may chose to buy an entry level machine, ready built.

Swings and roundabouts, i'm afraid, but I would highly recommend looking at buying some new kit.

do you perhaps have a friend who has some PC building experience? They could perhaps give you a little support with any potential new build. The trick is not to be scared of building a PC, just take your time and assemble all the tools you need, and you can't go far wrong. Good luck! :grin:

This machine was only $35 at the local computer recyclery so i don't feel like i'm out of pocket... funny that it's almost as fast with only 512MB as my mac is loaded with 1.5GB of ram... 

but i agree... it would be easier to go get another $35 machine and reinstall ubuntu than it would to mess around with a motherboard... in the end... i got this box with the intention of making it my media box... in fact it does everything i want it to do for that purpose so i'm not really pressed... i guess embarssed b/c i didn't know enough to look into the ram threshold before i got the machine...

---

