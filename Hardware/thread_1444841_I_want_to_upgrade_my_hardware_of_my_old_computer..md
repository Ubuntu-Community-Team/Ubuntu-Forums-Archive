---
title: "I want to upgrade my hardware of my old computer."
date: 2010-04-01
forum: Hardware
---

### Post by TheNerdAL on 2010-04-01
My computer is old, it had Windows XP when we first got it. I installed Ubuntu after it was slow, I liked it. But no desktop effects(which I really wanted) due to my SiS Card. I want to get a new video and graphics card(I think they are the same but I'm not sure) And maybe something else that would make my computer be like better. I would like get a list of hardware that I should upgrade. Thanks! :D 

PS: Should I get a professional to install the cards and hardware?

---

### Post by conradin on 2010-04-01
It would be best to give us some specs. CPU, motherboard, RAM, Case type, etc. You Could use the command lshw to get that info.

Second, I'm not sure if you've ever worked on electronics before. Grounding is extremely important. Either keep 1 hand on the metal of the case at all times, or get a grounding strap and connect yourself to ground.

also, unplug the power cord and then press the power button to dissipate most of the electrical charge quickly. 

keep in mind the minimum system requirements for the various distros and compare that to your current hardware. 

Finally, I'm not sure what your budget is, but a pretty nice computer can be purchased these days for 200 or more $. Doing many parts upgrades might not be cost effective.

---

### Post by TheNerdAL on 2010-04-01
```
adrian-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 370MiB
     *-cpu
          product: AMD Sempron(tm) Processor 3100+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.0
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:ed000000-ed0fffff memory:e0000000-e7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:e0000000-e7ffffff(prefetchable) memory:ed000000-ed01ffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:a000(size=256) ioport:a400(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:ed113000-ed113fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:ed114000-ed114fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:ed110000-ed110fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:ed111000-ed111fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:11:d8:44:db:e7
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.2 latency=32 maxlatency=11 mingnt=52 multicast=yes
             resources: irq:19 ioport:a800(size=256) memory:ed112000-ed112fff memory:20000000-2001ffff(prefetchable)
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:ac00(size=8) ioport:b000(size=4) ioport:b400(size=8) ioport:b800(size=4) ioport:bc00(size=16) ioport:c000(size=128)
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:ed100000-ed10ffff ioport:c400(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:16 memory:ed115000-ed1157ff ioport:c800(size=128)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

```

And no I never worked on electronics physically.

---

### Post by TheNerdAL on 2010-04-01
Mainly I just want a new video card. Also maybe more ram.

---

### Post by mastablasta on 2010-04-02
> **TheNerdAL said:**
> Mainly I just want a new video card. Also maybe more ram.
 
 
To me this kind of system anyalysis is confising as it doesn't say what sockets you have for RAM and graphics card.
 
If you still have winXP on then try to get informaiton on this by downloading and installing "Everest home edition". there is a similar linux command but i don't know it :-D
 
But basically you really need more ram and graphics card (i hope this is not a noteboook). Ram is porbably DDR or DDR2 (you should find that out - DDR is a bit odler and slower but it will do fine since you don't really notice the nano- and miliseconds). 1GB will be plenty and you will imediatelly notice a massive improvement on the system. 2GB is even better.
while the card needs to be is either PCI Express (PCI-e) or AGP. AGP is a bit older and these days it isq uite difficult ot find another motherboard for it, however there are still quite a few graphic card available for this socket. Unless you play some intensive games you oculd go with cheapest (most will advise Nvidia, but older ATI cards work nice as well) for arround 30 EUR (~40$-50$)

---

### Post by cascade9 on 2010-04-02
> **mastablasta said:**
> To me this kind of system anyalysis is confising as it doesn't say what sockets you have for RAM and graphics card.
 
If you still have winXP on then try to get informaiton on this by downloading and installing "Everest home edition". there is a similar linux command but i don't know it :-D

TheNerdAL- I pretty much argee with what masatblasta said (barring the stuff about DDR1 vs DDR2, but thats not important). A better idea of what hardware is in your box is needed.

'sudo apt-get install hardinfo' then 'hardinfo' (no quotes) for the linux program that does (some) of what  everest does. That would help a lot....

I'm pretty sure that box is using DDR1. With 370MB of system RAM, ou Really Want More RAM. Really. 

It might have an AGP port...or it might not. If it only PCI ports, getting a new video card is quite expensive...even AGP is more than PCIe. 


BTW, if you can find a cheap 2nd hand sound card (eg a creative sound blaster live) and have the PCIslot free for it, that would be nice as well. I've seen them go for under $10 these days.

---

### Post by Dayofswords on 2010-04-02
what what he gave us, i think it has 5 pci and one isa(i think on the isa)

not sure (it says "product: 661/741/760 **PCI**/**AGP** or 662/761Gx **PCIE** VGA Display Adapter"

please post the hardinfo!

ide for hard drives

this thing is quite old in computer years (i have an older one though =p)

dont get a pro just yet, lets see how far we can get ya

---

### Post by WTF_Shelley on 2010-04-02
Buying new ddr1 ram now is quite expensive, and finding a decent agp / pci graphics card is differacalt. it might be better to buy a new cheap pc. Ebuyers has a cheaper dualcore box with a big hard a nice amount of ram. for not a lot more then the parts you wanted and will have a new shiny warranty to go with it

---

### Post by ronnielsen1 on 2010-04-02
[QUOTEBuying new ddr1 ram now is quite expensive, and finding a decent agp / pci graphics card is differacalt][/QUOTE]

It costs about $50 for a 1G DDR1 stick around here and would be the biggest upgrade IMHO. Are you sure this pc doesn't have an AGP slot for video?

---

### Post by ronnielsen1 on 2010-04-02
> while the card needs to be is either PCI Express (PCI-e)

That box was before PCI-e AFAIK. Probably has a pci and agp slot

---

### Post by cascade9 on 2010-04-02
> **Dayofswords said:**
> what what he gave us, i think it has 5 pci and one isa(i think on the isa)


If that board has an ISA slot, I'll fall down with suprise. I cant recall the exact reason why ISA still appears but it does.... 

> **ronnielsen1 said:**
> That box was before PCI-e AFAIK. Probably has a pci and agp slot
 
 Probably it does only have PCI, or PCI/AGP, but its only sort of before PCIe- there are Sis 760GX chipsets with a 1xPCIe slot. Which means that unless you are happy hacking (as in physically hacking, not software) the card or the slot, you arent going to get video cards into the slot (barring a Matrox 550) 
 
 Asus K8S-MX (760GX chipset, single 1xPCIe)- 
 
 [http://www.asus.com/product.aspx?P_ID=0kP4nePr06XiYdYQ&templete=2](http://www.asus.com/product.aspx?P_ID=0kP4nePr06XiYdYQ&templete=2)
 
 The wonder that is the matrox 1x PCIe 550!- 
 
 [http://www.matrox.com/graphics/en/products/graphics_cards/g_series/g550pcie/](http://www.matrox.com/graphics/en/products/graphics_cards/g_series/g550pcie/)

> **WTF_Shelley said:**
> Buying new ddr1 ram now is quite expensive, and finding a decent agp / pci graphics card is differacalt. it might be better to buy a new cheap pc. Ebuyers has a cheaper dualcore box with a big hard a nice amount of ram. for not a lot more then the parts you wanted and will have a new shiny warranty to go with it

Buying new? Maybe, depends. I've seen some really nice deals on 2nd hand stuff...but I admit I know where to look.

---

### Post by TheNerdAL on 2010-04-02
I have installed Hardinfo, but what do you want information do you want me to show? There are a lot of options.

---

### Post by cascade9 on 2010-04-02
Doh :| 

I always forget that hardinfo cant actually show you what slots are in the machine....which is the info you are after. Maybe Dayofswords will have an iea I dont. 

I do hardware....the way I normally find out what slots are in the computer, whats free, etc, is to take the side of the case and eyeball it. Bit hard to do over the internet. 

If its a corporate computer (dell, etc) then the model number would help. If its a white box (built from non-corporate parts) then its going to take a screwdriver and a look. There should be a model number screenprinted on the motherboard.

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> Doh :| 

I always forget that hardinfo cant actually show you what slots are in the machine....which is the info you are after. Maybe Dayofswords will have an iea I dont. 

I do hardware....the way I normally find out what slots are in the computer, whats free, etc, is to take the side of the case and eyeball it. Bit hard to do over the internet. 

If its a corporate computer (dell, etc) then the model number would help. If its a white box (built from non-corporate parts) then its going to take a screwdriver and a look. There should be a model number screenprinted on the motherboard.

Guess I should get a professional? Or you can come over. :D

---

### Post by cascade9 on 2010-04-02
LOL, bit hard for me to get to the US. 

I dont really want to deal with the customs going in, even if I could ;)

---

### Post by TheNerdAL on 2010-04-02
My computer is from Compaq, if that helps.

---

### Post by cascade9 on 2010-04-02
Helps a little. Its probably this moherboard- 

[http://cgi.ebay.com.au/ASUS-K8S-LA-Salmon-HP-COMPAQ-SiS760-Socket-754-NEW-/230440542959](http://cgi.ebay.com.au/ASUS-K8S-LA-Salmon-HP-COMPAQ-SiS760-Socket-754-NEW-/230440542959)

If yuo know the model number then I would know for sure. This page should help you find it-

[http://h10025.www1.hp.com/ewfrf/wc/document?tmp_renderType=findModel&lc=en&dlc=en&cc=us&docname=c00004461](http://h10025.www1.hp.com/ewfrf/wc/document?tmp_renderType=findModel&lc=en&dlc=en&cc=us&docname=c00004461)

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> Helps a little. Its probably this moherboard- 

[http://cgi.ebay.com.au/ASUS-K8S-LA-Salmon-HP-COMPAQ-SiS760-Socket-754-NEW-/230440542959](http://cgi.ebay.com.au/ASUS-K8S-LA-Salmon-HP-COMPAQ-SiS760-Socket-754-NEW-/230440542959)

If yuo know the model number then I would know for sure. This page should help you find it-

[http://h10025.www1.hp.com/ewfrf/wc/document?tmp_renderType=findModel&lc=en&dlc=en&cc=us&docname=c00004461](http://h10025.www1.hp.com/ewfrf/wc/document?tmp_renderType=findModel&lc=en&dlc=en&cc=us&docname=c00004461)

Yup, That SiS Drive is there too. :P I think I can install the video card as I seen videos on Youtube of how to.

EDIT: I mean Ram.

---

### Post by cascade9 on 2010-04-02
Installing a video card is a bit more fiddy (normally you have to turn off the onboard video before you install the card) but not really any harder than installing RAM.

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> Installing a video card is a bit more fiddy (normally you have to turn off the onboard video before you install the card) but not really any harder than installing RAM.

All I know is that more ram, preferably 1 GB, makes the computer run more smoothly. But Video cards is for desktop effects. D: That's like $200 or more. I should just buy a new computer from System76 right?

---

### Post by cascade9 on 2010-04-02
$200? On a video card? Maybe, if your a gamer, for normal humans the $200 cards are just a waste. 

I've got a Athlon XP 2200+ (a bit slower than your 3100+ sempron) with 1GB and a nVidia GT6600- it runs KDE4.3 fine, so it should run compiz etc really well. 

GT6600, AGP, $30- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143027](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143027)

DDR1,. 512MB, $22-
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145026](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145026)

DDR1, 1GB, $35- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036)

If you can find a 2nd hand dealer in your area, and show them the prices you have here they should beat them (be carefull with the video card, they will try to give you a POS FX5200 or something even worse).

Of course, you can always got to system76 and buy a new system if you want. But there is lief in the old boxxen you have yet....

*Edit- BTW, you might be able to find a cheap socket 754 Athlon64 (3200+ or 3400+ would be nice) Yes, the number isnt that much higher than the 3100+ you have, but that is measured against celerons, the athlon 64 against P4s. It would be a nice upgrade, and let you run 64bit if you wanted as well. ;)

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> $200? On a video card? Maybe, if your a gamer, for normal humans the $200 cards are just a waste. 

I've got a Athlon XP 2200+ (a bit slower than your 3100+ sempron) with 1GB and a nVidia GT6600- it runs KDE4.3 fine, so it should run compiz etc really well. 

GT6600, AGP, $30- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143027](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143027)

DDR1,. 512MB, $22-
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145026](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145026)

DDR1, 1GB, $35- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036)

If you can find a 2nd hand dealer in your area, and show them the prices you have here they should beat them (be carefull with the video card, they will try to give you a POS FX5200 or something even worse).

Are those video cards supported for Desktop Effects? Also, I was talking about $200 for the Video card and more Ram. And the retailer I am thinking of ordering the computer from is a company that just sells computer with Ubuntu. :)

---

### Post by cascade9 on 2010-04-02
I know system76, even though I'll never see one 'in the metal'. Nice systems, bit more that I would pay- I build my own. 

All the FX (5-series) and up nvidia cards should do desktop effects fine....I know that the 6600GT does. For $70, with shipping, you could have all the desktop effects you want ;) 

Sure, it wouldnt be as fast as a newer computer, but it s lot cheaper.

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> I know system76, even though I'll never see one 'in the metal'. Nice systems, bit more that I would pay- I build my own. 

All the FX (5-series) and up nvidia cards should do desktop effects fine....I know that the 6600GT does. For $70, with shipping, you could have all the desktop effects you want ;) 

Sure, it wouldnt be as fast as a newer computer, but it s lot cheaper.

:O I might think about getting that. Hmm. I want to get into making my own computer too and get to know the parts. Is Intel Atom a good processor? It's on the System76 Meerkat models. Yeah, but I might just upgrade. I want my computer to run like new. It's pretty fast right now, but there are glitches due to my video. D:

---

### Post by cascade9 on 2010-04-02
From sombody who has used VIA onboard video- it sucks. Badly. Really badly. If it sucked any more, you couldnt open the door to the room that the computer is in. Linux or windows. 

Sis video cards arent much better with linux, but they were ok-ish on windows. 

As for the Atom- not my thing really, not enough guts. I perfer dekstops to have abit more power, for video and audio encoding. If all you do is lot of internet use, and some multimedia they are pretty good.If your planning on using it for multimedia, get the nvidia graphics model, not the intel graphics.

---

### Post by TheNerdAL on 2010-04-02
Lol, you are right, I found a 1GB Ram Memory for less than $30 so I can get both for like around $60. That's cheap. Does it matter which model goes in the memory slot? I think I heard that if you have an intel motherboard you go for an intel Memory card. Or is that just for processors?

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> From sombody who has used VIA onboard video- it sucks. Badly. Really badly. If it sucked any more, you couldnt open the door to the room that the computer is in. Linux or windows. 

Sis video cards arent much better with linux, but they were ok-ish on windows. 

As for the Atom- not my thing really, not enough guts. I perfer dekstops to have abit more power, for video and audio encoding. If all you do is lot of internet use, and some multimedia they are pretty good.If your planning on using it for multimedia, get the nvidia graphics model, not the intel graphics.

Yup, and Nvidia is cheaper too. :D

---

### Post by cascade9 on 2010-04-02
> **TheNerdAL said:**
> Lol, you are right, I found a 1GB Ram Memory for less than $30 so I can get both for like around $60. That's cheap. Does it matter which model goes in the memory slot? I think I heard that if you have an intel motherboard you go for an intel Memory card. Or is that just for processors?

Be carefull with teh RAM- DDR2 is cheaper, but it wont run in your system. Its got to use DDR1 (normally written as just DDR). 

It wont matter what sitck is in what slot on your computer. 

If you have an intel chipset/motherboard, you have to use intel CPUs, but Intel doesnt make memory.

---

### Post by TheNerdAL on 2010-04-02
> **cascade9 said:**
> Be carefull with teh RAM- DDR2 is cheaper, but it wont run in your system. Its got to use DDR1 (normally written as just DDR). 

It wont matter what sitck is in what slot on your computer. 

If you have an intel chipset/motherboard, you have to use intel CPUs, but Intel doesnt make memory.

Oh thanks for that. I was about to get one that has DDR2 on it. I found this stick: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820236112](http://www.newegg.com/Product/Product.aspx?Item=N82E16820236112) I really want to get into this kind of stuff! :D

---

### Post by TheNerdAL on 2010-04-02
The GT6600 video card is DD3, does it work on my motherboard?

---

### Post by cascade9 on 2010-04-03
IMO the easiest way to get into the hardware is with stuff you really dont care that much about. Not that its a problem to work on the g'ood' stuff but its always nice to have a box you can play with, but if things go wrong you can walk away from and boot up a different computer. 

> **TheNerdAL said:**
> The GT6600 video card is DD3, does it work on my motherboard?

As long as you have an AGP x4/x8 slot, it will work fine. The memory on the video card isnt like memory you install into the motherboard. With the motherboard RAM, the chipset needs to recognise the RAM (and it needs to fit, SDRAM/DDR1/DDR2/DDR3 dont interchange- only 1 type of RAM will fit into the slot). With video card RAM, its used internally by the card, and the interface is the PCI/AGP/PCIe slots.

---

### Post by TheNerdAL on 2010-04-03
I have a PCI, so any video card that is PCI works?

---

### Post by cascade9 on 2010-04-04
No AGP? Pity- PCI cards tend to be more expensive than AGP (and PCIe is cheaper still) 

Pretty much any PCI card should work- but a lot of them wont be that much better than the VIA onboard video. There are lots of PCI nVidia MX 4000 cards around, and they ate back to 2003. There are PCI ATI cards around that are just as old....

---

