---
title: "Beginner : would I have problems with this computer?"
date: 2010-10-19
forum: Hardware
---

### Post by polype on 2010-10-19
First, sorry for my poor english...

i'm a a totally beginner in Linux
I've installed U 10.04 two months ago and I like it a lot

Now, I've decided to buy a new computer and to install only Ubuntu,
(maybe also WindowsXPsp3 in Virtual Box: only for a language course that does not work with Wine)

I ordered this PC to-day,
Do you think this configuration would work without too many problems with Ubuntu 10.10 64bit

processor: AMD Phenom II X4 965 3,4 GHz AM3 Boxed With Cooler

mobo: ASUS M4A88T-M/USB3 (Socket AM3-AMD 880G-MicroATX-DDR3)

memory: Kingston 8GB (2x 4GB) 1600MHz DDR3 HyperX

videocard: ASUS nVidia GeForce 220 GT 1GB passive

hardisk's
1. Western Digital 600GB SATA III 10000RPM 32MB VelociRaptor
2. Western Digital 1TB SATA II 7200RPM 32MB Caviar Blue

case : Cooler Master Sileo 500 + 500w

also DVD writer Samsung SATA 22x DL


Thank you for your time and your  help
P.

---

### Post by Lazaruss on 2010-10-19
as long as you get the right version (i guess AMD 64bit)

graphics should work, nvidia do provide proprietary drivers if the ubuntu ones don't work.

if relevant, what networking devices has it got?

---

### Post by cascade9 on 2010-10-20
Should all work fine (though I have to laugh at the number of times I see ATI onboard video chipset motherboards being sold with a video card....silly, they should have got a 870 chipset motherboard) 

> **Lazaruss said:**
> as long as you get the right version (i guess AMD 64bit)

if relevant, what networking devices has it got?

Realtek RTL8111E Gigabit LAN. 

You donthave to run AMD64 on a 64bit system, 32bit will work (and with a PAE kernel it will see all the RAM  as well). That said, I'd run 64bit on that system every time myself.

---

### Post by polype on 2010-10-20
> **cascade9 said:**
> Should all work fine (though I have to laugh at the number of times I see ATI onboard video chipset motherboards being sold with a video card....silly, they should have got a 870 chipset motherboard) 

Realtek RTL8111E Gigabit LAN. 

You donthave to run AMD64 on a 64bit system, 32bit will work (and with a PAE kernel it will see all the RAM  as well). That said, I'd run 64bit on that system every time myself.


Thanks for your answers

but I do not understand your "ATI onboard video chipset motherboards being sold with a video card....silly" : I'm no specialist !

And also, I'm not sure what you mean by PAE and may I ask a last question:
Whic Ubuntu should I download ?

Regards,
P.

---

### Post by TBABill on 2010-10-20
PAE means physical address extension. It allows your computer to "see" and use the full memory of your system up to 64GB. [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
 
I would recommend 64 bit for a powerful machine like that. Adobe Flash and other apps seem to be working well under 64 bit. However, some apps (Frostwire is one that comes to mind) are not available in 64 bit so you occasionally have to force the system architecture to use 32 bit apps. It's not a big deal but you may have to ask for assistance here or read up via a Linux or Ubuntu book for those few times. Plenty of help here to get you over those hurdles if you need it.
 
I would recommend you use 10.04 LTS for now. I have the same Realtek RTL8111 wireless adapter and it will NOT work with 10.10 right now. My Broadcom on my laptop works great, but the Realtek will simply not connect to any network, although it sees them all. I even tested Mint 10, based on Ubuntu 10.10, and it did not work either so I know it is not the download, the CD, etc. Wired works fine on it, wireless does not. 10.04 works perfectly. I'm sure that will be sorted out soon, but I wanted you aware ahead of time in case you get it and try to install 10.10 and become frustrated.

---

### Post by cascade9 on 2010-10-20
@ TBABill- The Realtek RTL8111E Gigabit LAN I quoted above is the onbaord, wired only version. 

^(%& realtek having both wireless and wired adapter with the same name :| 

AFAIK the wired 8111E should work fine. 

> **polype said:**
> Thanks for your answers

but I do not understand your "ATI onboard video chipset motherboards being sold with a video card....silly" : I'm no specialist !

Your motherboard is using an ATI 880 chipset, which has intergrated video (you can see the DVI and/orVGA ports on the backplane if you look). The extra engineering in the chips and motherboard isnt free, in any way....

I just have a generally high 'WTF' factor at the number of systems I'm seeing, some of which have been branded 'high perfromance', that are using AMD intergrated video chipsets (880, 890GX) with a video card, a lot of them with microATX motherobards in full ATX towers. 

Its just...weird. I can see how it happens, and all the AMD 8XX chipsets all have the same basic specifications on paper.....its just somemthing that gets to me. 

Dont worry, theres nothing wrong with your system, I just have a different idea as to what to get to whoever specified the parts in your system. Or prehaps even the same idea, just his/her boss said 'drop the 890FX motherboard for a 880, we're getting a huge order for them and its just easier to spec all the systems with the same basic boards " .

---

### Post by TBABill on 2010-10-20
It would be my luck to now have to wonder when someone posts about the Realtek card I have whether they mean wired or wireless....one more thing to consider before I respond to them. Thanks for the clarification. I guess the "e" differentiates it from wireless?

---

### Post by cascade9 on 2010-10-21
Not just the 'E'. There is 'B', 'C'. 'CP', 'D', 'D(L)' and probably other variants as well. To be honest, I'm not sure which version is wireless, I had assumed before now that it would get a letter as well (RTL 8111W would have almost made sense) *shruggs*. 

Very annoying.

---

### Post by polype on 2010-10-21
> **cascade9 said:**
> Not just the 'E'. There is 'B', 'C'. 'CP', 'D', 'D(L)' and probably other variants as well. To be honest, I'm not sure which version is wireless, I had assumed before now that it would get a letter as well (RTL 8111W would have almost made sense) *shruggs*. 

Very annoying.


Thanks very much all of you for your kind help
I will be back soon for my next question ;)
P.

---

