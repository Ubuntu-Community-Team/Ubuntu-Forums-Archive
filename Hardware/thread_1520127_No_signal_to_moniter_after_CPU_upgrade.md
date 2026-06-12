---
title: "No signal to moniter after CPU upgrade"
date: 2010-06-29
forum: Hardware
---

### Post by Nick_Jinn on 2010-06-29
Probably not an Ubuntu issue really, but there are lots of techies here who like to help people, so it seems like a good place to ask. 


So I have this motherboard.

[http://www.skyline-eng.com/index.cfm?fuseaction=product.display&Product_ID=6886](http://www.skyline-eng.com/index.cfm?fuseaction=product.display&Product_ID=6886)


Acer Aspire Ast180 desktop tower.



In theory this motherboard should support dual core Athlon x2 chips right?

> 
**CPU (Processor) support:** 
 
[LIST]
[*] AMD AM2 Athlon 64 x 2 or Athlon 64 or Sempron (socket 940)
[/LIST]
So I took out the Athlon 64 single core and put in a dual core 2.6 ghrz. I upgraded the cooler slightly, and the fan is blowing and things are looking good.....until I notice that there is no signal to the monitor.


So whats wrong? Does it actually not support this? Do I need a firmware update? How do I do that if I dont get a screen? Did I mess up the motherboard by getting a few dabs of superglue on it? I wouldnt think it would as it doesnt conduct electricity.

It was such a pain in the *** I dont really feel like switching back before trying everything.

---

### Post by robert shearer on 2010-06-29
Find and download the motherboard manual.

Read through it and take note of any settings for jumpers on the board.

Often these are configured for the bus settings as per the cpu the board shipped with.
Yes the board may support the cpu you are trying but with different FSB etc.

So, do read the mobo manual and only change things if you feel you have understood what it is you're doing.

If unsure post back with more details.

Also, are there any beep codes on switch-on with the new cpu installed ?
Are you using a graphics card or the boards graphics?. May simply be that you need to run the monitor from the inbuilt graphics while you set up bios for first boot graphics device.
Again, read the manual for the mobo.

---

### Post by Nick_Jinn on 2010-06-29
lol

I feel like such a noob. I dont even know what that stuff is....I do know that some of the same model Ast180 Aspire come with dual cores out of the box, but this paticular one came with an Athlon single core instead of dual core or Sempron.


I found a download but they charge for it. I am still hunting for a free manual.


Maybe I can call the company tomorrow or the next day, but any ideas I could try until then would be appreciated.


What exactly can I do to the computer in its present state, short of putting the old CPU back in and tinkering with it from there?

---

### Post by VeeDubb on 2010-06-29
Disclaimer:  You're not going to like my answers.  Sorry.

1. Can't say for certain if the CPU you gut is supported or not because you haven't said which CPU you got.  I'm pretty sure that what you listed could have been made for more than one socket, and even if you get the CPU in the socket, it may not be the right one.

2. Yeah, it's 100% possible that a BIOS upgrade (firmware) would allow newer CPUs as long as they are for the same socket.  However, if it's not posting because of the new CPU, you have absolutely no choice but to put the old one back until you get it updated.

3. Since that motherboard is an Acer, and Acer doesn't generally sell bare motherboards, I'm not able to find any real information, and you're going to have a heck of a time finding a bios update if there is one.

4. This is the big one.  Upgrading the CPU should be extremely easy, and take about 5 minutes.  If it was "such a pain in the ***" you may have done something VERY VERY wrong.  Maybe several things.  If you've never changed a CPU before, it's entirely possible that you did something very bad, like put it into a socket that wasn't meant for it or put it in the wrong way.  A CPU should literally drop into the socket with absolutely no presure beyond the force of gravity.  That's not an exaggeration.  If gravity isn't enough to put it in the socket, you did something very wrong.  (It is however a good idea to apply some downward pressure while flipping the lever that lock the CPU in place)

5. Depending on where you got the superglue, yes.  You may well have caused permanent and irreparable damage.  Please explain what you were doing with super glue, which should NEVER be used in this kind of application.

6. It's also possible that the new CPU is simply defective.


As far as moving forward, there are really only a couple things you can do.

1. Post a link to where you bought your CPU, so we can see exactly what it is.

2. Explain more about the superglue.

3. Re-seat your memory, all cables, and all PCI/AGP/PCIe cards.  Something may have become partially disconnected when you were installing other stuff.

4. Remove the new CPU and put the old one back in.  Check for bent pins caused by incorrect installation and/or physical defects.  Install firmware updates if available and try again (be aware that incorrectly installed firmware updates will brick your motherboard semi-permanently) and if there's no bent pins, no firmware updates, and your CPU should be compatible, you'll have to exchange it as DOA.

---

### Post by Nick_Jinn on 2010-06-29
lol

Im not THAT oblivious. I didnt try to superglue the CPU into the socket or anything. lol.....The images you must be having right now.



No, I didnt get superglue anywhere near the socket. The CPU DID plop into the socket easy as pie. The difficult part was the cooler. It was a narrow fit and this model of cooler was a pain in the ***. Every time I got close the thermal paste would grab onto the CPU, so it took some doing in a tight space to lock it in without pulling it out of place.

The super glue was for the the plastic part that clamps the cooler down, it didnt get anywhere near any connectors or the socket holes.


lol. Im not that much of a dumbass. It is the first CPU I ever changed, but I am a lot smarter than whatever you are imagining. I have common sense. The difficult part was getting the cooler in, and mostly because of the tight space and the thermal paste.



The CPU is an Athlon 2 dual core 2.6 ghrz. I have seen this motherboard ship out with this CPU before at similar if not faster speeds. The CPU should be supported.




But no, I didnt go super gluing the CPU in backwards. Its in exactly right and its an AM2 chip in an AM2 board, 940 pin socket for a 940 pin (AM2 not 940 socket) CPU.



Everything fits perfectly, though the cooler was a pain in the *** to clamp down.






So any tips from here?

---

### Post by VeeDubb on 2010-06-29
> **Nick_Jinn said:**
> So any tips from here?

Absolutely!

Now that you've eliminated all the "special stupid" options, we're only left with a couple of things.

The bad news is that most one of them involve removing the new CPU and probably putting the old one back in.

I would still try to re-seat everything.  It is not only possible, but fairly likely that the trouble you had getting the new cooler attached caused one of your memory DIMMS to pop partially out of place, which can keep the system from posting.  Takes two minutes to check and fix, and it's the only one that doesn't in.

As one last sanity/stupidity check double check to make sure you didn't do something like forget to connect the power cable for the CPU fan to the CPUfan connector on the motherboard.  A lot of boards won't post if there's nothing plugged in there.  I've personally done this, although only once....

You could also double check that you didn't do something silly like plug the monitor cable into the on-board video after disabling it and installing a separate video card.  As idiotic as that is, I did that once too.....

After that, the only two things are a BIOS update, which you won't be able to do until you get the old CPU back in there, or a defective CPU.

---

### Post by VeeDubb on 2010-06-29
> **Nick_Jinn said:**
> I am a lot smarter than whatever you are imagining. I have common sense.

Just for the record, no offense was intended.  I've seen some very intelligent people do some really stupid stuff inside their computers, and even managed a few myself along the way.

---

### Post by Nick_Jinn on 2010-06-29
No offense taken. I could just imagine you visualizing me trying to super glue the CPU in backwards though....haha. 


The fans are running. I can hear them at start up and I can see them spin. The CPU and video cards both have spinning fans which is a good sign that things are sort of working still.

Video is plugged into the video card. VGA, the only VGA plug in the computer.


I guess it wouldnt be the end of the world to put the old CPU back in, but I got the thermal paste in just perfect and its a tight space for latching that cooler down.....I lost the screws so I glued the plastic housing for the cooler to the motherboard, and I was worried that maybe that did something. Its probably fine and will work when I go back to the old CPU.


But if there is anything I can try before putting the old CPU back in I would rather try that FIRST and then switch it back as a last resort.



I may just get a new motherboard and power supply instead and put my dual core athlon in there...I have a different case and everything......Do Phenoms use the same socket as Athlon? I would love a motherboard that would support my Athlon today and Phenom when I get my settlement money for a wrongful arrest.

---

### Post by VeeDubb on 2010-06-29
> **Nick_Jinn said:**
> ...Do Phenoms use the same socket as Athlon? I would love a motherboard that would support my Athlon today and Phenom when I get my settlement money for a wrongful arrest.

Other than the interesting implied story there, the answer is not really.  They only sell phenoms for the AM2+ and AM3 sockets, and I really wouldn't recommend going with an AM2+ at this point since it's on the way out.

For the bargain concious, this motherboard - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130228](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130228)

And this CPU - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103704](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103704)

Give great performance at a very reasonable total cost.  I recommend those, because that's what I've been using for a couple of months now, and I couldn't be happier.  Very good cost/feature ratio.


On a side note, yeah, gluing the CPU cooler bracket to the motherboard certainly could cause problems.  There's a lot of stress on those brackets as you discovered, and having it glued to the surface instead of attached properly could cause problems.  Sadly, the best way to test this would be to put the old CPU back in.  I just don't see any way you're going to avoid it.

---

### Post by cascade9 on 2010-06-29
> **VeeDubb said:**
> Just for the record, no offense was intended. I've seen some very intelligent people do some really stupid stuff inside their computers, and even managed a few myself along the way.
 
 +1...on all the above. 
 
 Stupid things are stupid, but that is only obvious once you know they are stupid. ;) 

BTW, neat post #4. One thing I would add, at the beginning-

Are you getting the BIOS initialised single beep? If not, then of course your monitor wont come on, the BIOS doesnt support whatever CPU you have installed. Or somethign else nasty has happened, but that is far less likely than it being a pure BIOS issue. 

> **Nick_Jinn said:**
> The CPU is an Athlon 2 dual core 2.6 ghrz. I have seen this motherboard ship out with this CPU before at similar if not faster speeds. The CPU should be supported.

Lots of Athlons, and IMO the CPUs that have the same spec that you have seen ship with the same motherboard would be Atlhon X2, not Atlhon II.  

Its more than possible that Acer had a newer version of the BIOS in systems that shipped with dual-core CPUs. 

BTW, if you check the ECS site you will find this- 

[http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=820&CategoryID=1&DetailName=Feature&MenuID=21&LanID=9](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=820&CategoryID=1&DetailName=Feature&MenuID=21&LanID=9)

That is the 'non-crippled' version. There is probably virtually no difference between the boards (I havent had a good poke to check), but ECS has made a slight variation on the model name to suit Acer. Seen them do that sort of thing before......

Anyway, even according to ECS, that board only supports AM2, not AM2+ 
> **Nick_Jinn said:**
> But no, I didnt go super gluing the CPU in backwards. Its in exactly right and its an AM2 chip in an AM2 board, 940 pin socket for a 940 pin (AM2 not 940 socket) CPU.

All the Athlon II CPUs I've seen have been AM3, not AM2 or AM2+. 

> **Nick_Jinn said:**
> I may just get a new motherboard and power supply instead and put my dual core athlon in there...I have a different case and everything......Do Phenoms use the same socket as Athlon? I would love a motherboard that would support my Athlon today and Phenom when I get my settlement money for a wrongful arrest.

Like VeeDubb said, there are only AM2+ and AM3 Phenoms. You should be able to run a AM2 CPU in an AM2+ socket, and AM3 will run in some of the AM2 boards, and most of the AM2+ boards. But you cant run AM2/2+ in an AM3 socket (as the AM2/2+ CPUs only have a DDR2 controller, and wont work with AM3s DDR3) 

So you could get an AM2/AM2+ board by a decent manufacturer (ie non-corporate) but again, they are going out now....

You could get an AM3 board, but then you would need to buy DDR3. 

Its also possible that you could crossflash the BIOS from the non-crippled ECS version onto your board, but that is risky..and if you have an Athlon II then I think it wont work anyway. 

BTW, I'd take a gigabyte GA-770T-USB3 over that MSI myself, but I'm, seriously unhappy with my current MSI board and I just build a really nice system with the gigabyte for my housemate so I am biased. 

One other thing- the gigabyte (and the MSI if you get the right BIOS) will 'unlock' cores. You can turn a semperon into an athlon II dualcore, and phenom II dual/triple cores into quads.

---

### Post by Nick_Jinn on 2010-06-29
You people are great. I love the Ubuntu Philosophy of helping others. I think this philosophy should replace our current one.



What is the problem with buying an AM2+ if its on its way out? Shouldnt it be a bargain? What would the problem be for me if they discontinue it?

Being able to use DDR2 RAM would also save me money as its one less thing to buy. 



Those motherboards look like good options, but I would really like to see a 3rd or 4th PCI slot.

---

### Post by VeeDubb on 2010-06-29
Well, I guess there isn't anything wrong with it, as long as you're aware that it's what you're doing.

For me, I recommended avoiding it because you're already asking about future upgrades, so I figure you're a bit like me in terms of wanting to keep things up to date, and if that's the case, you're not going to be happy with a last gen board.

---

### Post by Nick_Jinn on 2010-06-29
Money is a factor though. I only have a few hundred to work with total, not a few hundred for each set of components. Back compatibility with my current hardware and chip is important for the time being. 

AM2+ will support a Phenom quad fairly well right? 


Is this a decent board?

[http://www.directron.com/lpdk790gxm2rs.html?gsear=1](http://www.directron.com/lpdk790gxm2rs.html?gsear=1)




Anyway, is there anything else I should try to get my current AM2 to support an Athlon dual core?

---

### Post by VeeDubb on 2010-06-29
[QUOTE=Nick_Jinn;9527089]AM2+ will support a Phenom quad fairly well right? 
/QUOTE]

Yes and no.  Today, you certainly can get AM2+ Phenoms.  

The issues is whether or not you'll e able to get one a year from now.  You won't pay significantly more for a low-end AM3 CPU than you would for a comparable AM2+, but doing so will give you a LOT more time in which to upgrade.

I would not buy that motherboard.  It's significantly more than either of the two boards that have been recommended, and doesn't offer any particularly improved features.

Just for grins and giggles, tell me what features you want in your motherboard, and I'll price out what I would buy.

---

### Post by cascade9 on 2010-06-30
Ahhh, DFI. Great brand, but I wouldnt get that board either. You've got a video card, and you dont need onboard video. You could get a 770 chipset (no video) board cheaper than that. 

> **Nick_Jinn said:**
> What is the problem with buying an AM2+ if its on its way out? Shouldnt it be a bargain? What would the problem be for me if they discontinue it?

Being able to use DDR2 RAM would also save me money as its one less thing to buy. 

Umm.....you are well into opnion/debatable 'facts' here. But my take (and its quite possible that VeeDubb will disagree) is that AM3 should have a longer upgrade path than AM2+, and DDR2 is going to go up in price compared to DDR3 in the future.  DDR3 is faster, and cooler (temp, not geek points) than DDR2 as well. 

The other advantages to an AM3 motherboard are SATAIII and USB 3.0. SATAIII isnt really needed now, unless you want to spend top dollar on a SSD, but as SSDs get faster, and cheaper, its a nice option.  Pretty much the same with USB 3.0, though it might be more usefull right now than SATAIII. 

BTW, not all AM3 motherboards have USB3.0 or SATAIII. You need a SB8XX southbridge or a SATAIII controller chip on the board for SATAIII (some AM3 boards have th older SB7XX southbridge). SB8XX is a much better option, the controller chips tend to have crappy linux support. USB 3.0 should be done from the southbridge in the future, but as of now I'm yet to see that, so far its mainly been from NEC USB 3.0 chips, which works fine with linux, well, it works fine here anyway....not that I've tested for speed, I've just plugged in a flash drive to see if linux works with the NEC chips.  

AM2+ isnt really a bargin now. It is cheaper than AM3, but the features sort of make up for the extra cost. 

BTW, like I said before, you dont have to use AM2+ CPUs in an AM2+ motherboard. The better brands do have AM3 CPU support on AM2+ motherboards, eg- 

[http://www.gigabyte.com/support-downloads/cpu-support-popup.aspx?pid=3302](http://www.gigabyte.com/support-downloads/cpu-support-popup.aspx?pid=3302)

Some of them (like the above) even support Phenom II X6 CPUs. 

> **Nick_Jinn said:**
> Those motherboards look like good options, but I would really like to see a 3rd or 4th PCI slot.

PCI is on its way out as well. Not as fast as AM2+, but slowly, things that were PCI in the past are moving to PCIe. Unless you've got 3-4 PCI cards you want to use right now, PCIe slots will be more useful in the future than PCI. 

I cant imaging that you would need 3-4 PCI slots anyway- onboard sound is pretty good these days and sound cards are moving to PCIe anyway. Same with network cards, and as for RAID cards- PCI is too slow @ 133MB/sec maximum speed. HDDs are pushing that speed as single drives now, and SSDs are already way past that. RAIDed modern SATA HDDs on a PCI RAID card will make the PCI interface the bottleneck. :(

---

### Post by VeeDubb on 2010-06-30
> **cascade9 said:**
> You could get a 770 chipset (no video) board cheaper than that. 

My point exactly.

> **cascade9 said:**
> Umm.....you are well into opnion/debatable 'facts' here. But my take (and its quite possible that VeeDubb will disagree) 

Nope, I don't think I could find anything to disagree with there at all.   You and me, pretty much talkin' the same language here.  Go AM3 because the OP sounds like he wants bang for the buck AND long-term upgradablity.

> **cascade9 said:**
> BTW, not all AM3 motherboards have USB3.0 or SATAIII. 

It's also worth pointing out that not all of them support DDR3, although technically they're supposed to.  Technically, the hardware in any AM3 board will, but many don't have support in the firmware.  

> **cascade9 said:**
> AM2+ isnt really a bargin now. It is cheaper than AM3, but the features sort of make up for the extra cost. 

Yup, still on the same page there.

> **cascade9 said:**
> PCI is on its way out as well. Not as fast as AM2+, but slowly, things that were PCI in the past are moving to PCIe. Unless you've got 3-4 PCI cards you want to use right now, PCIe slots will be more useful in the future than PCI. 

I'm not 100% sure I agree with you on this one.  PCI is going away so slowly, and PCIe is gaining so slowly (except in the video card department where it crushed AGP and PCI within a year) that I'm not sure if it's ever going to replace them, or if they'll both get replaced by whatever comes next.  Either way, you're right that it shouldn't be a concern unless the OP already has a bunch of PCI cards he wants to use, and don't come onboard with a 770 chipset.

---

### Post by Nick_Jinn on 2010-06-30
I kind of want an AM2+ to save money in the moment. Like I said, I am expecting 16k from the federal government for an unlawful mass arrest, but for the next 6 months I am worried about making rent. Saving money (in total, in the immediate here and now) is my top priority.

The bad news...So I switched back to the old CPU and I still get no video. That sucks. Now I dont even have a working computer. All I have is my 'Edge" which has a 10 inch e-ink reader and a 10 inch android tablet. I can barely attend to online business with it and I make all my money online.

So I have no choice. I need to build a new computer.


One route I could go is to just replace the acer AST-Motherboard, NOT superglue the heat sink attachments to the motherboard like a dumbass, and go back to what I had which MIGHT support the dual core. Its kind of a nice motherboard despite being on the smaller side. It has these cool sliders that replace the need for screws. I like that.

Or if I could get a better motherboard I could go that route also....In fact, I might as well. This is a smaller/mid sized motherboard.....not a sub-compact for those semi-portable desktops, but a smaller sized regular tower. There is probably a word or abbreviation for that sized motherboard.

I would be happy to get a motherboard with at least 2 PCI slots that fits into my Acer case, or I would prefer more upgrade slots if I need to get a bigger case (I would like a bigger case if I can afford it, especially if it has those slide locking mechanisms).



I do already have a bunch of old PCI stuff.....a semi-decent wireless PCI card, though I also have a USB card. I have a 5 USB expansion PCI card. I have a Ethernet Modem PCI card (If needed). I have a kick *** sound card, and I have a very nice video card for PCI-e.

I have 6gb of DDR2 RAM, 4x 1gb and 2x 512.

I have a TB SATA HD, and a 320gb PATA HD. It would be nice to use both OR the TB SATA + 160GB SATA I also have.

I have a Multi-burner with DL capability.

I have an Athlon x2 2.6 dual core.


So I want to use as much of the above as possible. I need to upgrade the motherboard but I want it to support my current chip as well as support a Phenom in the next year or two.....If the computer gets outdated again in a few years its not the end of the world, because I will hopefully be rich or have more money by then. I need to survive the next 6 months and then I have a lot of opportunities opening up. I am not looking for the ultra long term investment.

If the Motherboard fits in my case, that would be a good thing. I could survive with 2 PCI in a pinch.

If I have to buy a new case and power supply, I would prefer a bigger case that has room for my liquid cooler that didnt fit in my current setup, and a motherboard that supports my dual core Athlon and my 6gb of DDR2 RAM.


I am more than happy to buy peoples used stuff too.




Any tips for me?



PS, a mid tower is fine as long as its thick enough to support my cooler.

---

### Post by cascade9 on 2010-06-30
@ VeeDubb- we agree? Excelent, that means you are right :biggrin:

> **VeeDubb said:**
> 

Not just  a firmware issue, DDR2 and DDR3 has different notch position- 

[http://en.wikipedia.org/wiki/File:Desktop_DDR_Memory_Comparison.svg](http://en.wikipedia.org/wiki/File:Desktop_DDR_Memory_Comparison.svg)

[QUOTE=VeeDubb;9529253I'm not 100% sure I agree with you on this one. PCI is going away so slowly, and PCIe is gaining so slowly (except in the video card department where it crushed AGP and PCI within a year) that I'm not sure if it's ever going to replace them, or if they'll both get replaced by whatever comes next. Either way, you're right that it shouldn't be a concern unless the OP already has a bunch of PCI cards he wants to use, and don't come onboard with a 770 chipset.

Point. Very debatable though, and lets just avoid that now ;) 

> **Nick_Jinn said:**
> 

The bad news...So I switched back to the old CPU and I still get no video. That sucks. Now I dont even have a working computer. All I have is my 'Edge" which has a 10 inch e-ink reader and a 10 inch android tablet. I can barely attend to online business with it and I make all my money online.

So I have no choice. I need to build a new computer.

Crap. :( My condolences. 

> **Nick_Jinn said:**
> I would be happy to get a motherboard with at least 2 PCI slots that fits into my Acer case, or I would prefer more upgrade slots if I need to get a bigger case (I would like a bigger case if I can afford it, especially if it has those slide locking mechanisms).

Acer case could make things an issue, sometimes corporate manufacturers have non-standard mounting holes, and/or non-standard switch/led pinouts. 

> **Nick_Jinn said:**
> I do already have a bunch of old PCI stuff.....a semi-decent wireless PCI card, though I also have a USB card. I have a 5 USB expansion PCI card. I have a Ethernet Modem PCI card (If needed). I have a kick *** sound card, and I have a very nice video card for PCI-e.

Your sound card has a super-power of being to withstand being beaten up and not feeling it? o.O Pity your motherboard didnt have the same power (sorry, bad joke) 

I can see why you would want a few PCI slots then. Funny thing is, all the AM2+ boards I'm seeing now are limited to 3 PCI slots....but you can get 4 on AM3. Odd, eh? 

Apart from the USM ports, usefull (I really dont see the point of a PCI USB card on motherboards that support 8+ USB 2.0 ports, but I dont have many USB devices).  

> **Nick_Jinn said:**
> I have 6gb of DDR2 RAM, 4x 1gb and 2x 512.

I have a TB SATA HD, and a 320gb PATA HD. It would be nice to use both OR the TB SATA + 160GB SATA I also have.

I have a Multi-burner with DL capability.

I have an Athlon x2 2.6 dual core.

All that should be fine on all teh AM2+ boards I've seen. I'm yet to see any that dont have an IDE port (for the 320GB PATA and burner, if it is IDE) and they all tend to have at least 4 SATA ports, and 4 DDR2 slots. 

> **Nick_Jinn said:**
> Or if I could get a better motherboard I could go that route also....In fact, I might as well. This is a smaller/mid sized motherboard.....not a sub-compact for those semi-portable desktops, but a smaller sized regular tower. There is probably a word or abbreviation for that sized motherboard.

MicroATX. Which means you (probably) wont be able to get a full ATX motherboard in there. Well, unless there is plenty of space at the bottom of the case...it wouldnt be the 1st time I've seen a mircoATX motherboard in a full ATX corporate case. 

Just so yuo know, there are some really good 'open box' deals around, like this- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138168R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138168R)

Just over $40 shipped......very nice ;)

---

### Post by Nick_Jinn on 2010-06-30
Awesome. I appreciate the help I get from all of you. I get better help here than I would get from Acer for $130 an hour. lol.

Yeah, I am ready to just walk away from the Acer and sell it for parts....I have another Acer laptop thats also having problems....I get it back from the shop in a few weeks, but thats not good enough.


That is a perfect motherboard. I can get by with 3 PCI as long as I dont have 2. The price is right.



Part of me wants to build this thing myself, the first one I ever built from scratch. Another part worries about whether I will do something stupid again....I really thought superglue would be fine if It didnt touch any connectors. Doooh!

So I may just buy a new case and new motherboard and build it from scratch....should be pretty easy right? I finally got the hang of changing CPUs and everything else is easy to swap out. Just screw in the motherboard and plug a few odd cords into the correct pins? I might get stuck there, but it doesnt sound too hard.


Then again, I may just go for a bare bones computer if there are any around at a good price. If I do that I might jump right into a phenom quad if the total is around $300.


Should a regular mid tower be the right size for that mobo? I would really like something with those slide locking slots, but its not really essential.


Im totally willing to buy old hardware too if somebody wants to offer me a good deal on something. I use paypal.

---

### Post by VeeDubb on 2010-06-30
> **Nick_Jinn said:**
> A If I do that I might jump right into a phenom quad if the total is around $300.


How about a brand new AM3 motherboard with DDR3 support, 4GB of DDR3 with room to upgrade later, and a brand new AM3 Atholon II X2 dual core CPU that's at least as good as the one you've got, 3 PCI slots, and basically room to attach everything you listed for $200.97?  

Or how about all the exact same stuff but with a quad core Phenom for $272.98?

I'm not selling any of that stuff myself.  That was pricing it out on my favorite hardware site.  What you're talking about does NOT need to be expensive.

As far as used parts to get you by for now, that never turns out to be free.  I could probably dig a spare mobo and CPU out of my pile-o-parts, but it would need DDR1, and I gave the last of my spare DDR1 to my brother a couple months ago.  And buying DDR1, now that it's "legacy" hardware is prohibitively expensive.

---

### Post by gordintoronto on 2010-06-30
Do you understand that this: "The CPU is an Athlon 2 dual core 2.6 ghrz" did not identify the CPU? CPUs have model numbers.

I suggest the PCMech site for this kind of hardware assistance. Also, use newegg.com to research computer components.

You can get an excellent CPU for less than $100, and a matching motherboard for about the same.

---

### Post by Nick_Jinn on 2010-06-30
> **VeeDubb said:**
> Or how about all the exact same stuff but with a quad core Phenom f or $272.98?.

Yeah? What motherboard is it? Its not the Foxconn is it? I heard rumors that they sabotaged the bios to not support aspects of linux....I dont know if its credible though.

But yeah, I would totally go for that if it came with the RAM for that price.



I dont know the model number of the CPU I was using, but its irrelevant now because my computer is toast....I dont think it was THAT obvious that superglue would ruin a motherboard if it didnt touch any of the connectors, but I guess I am a little bit of a dumbass.



Links to bare bones computers will be appreciated.

---

### Post by Yellow Pasque on 2010-06-30
If you have DDR2 and a nice AM2 CPU already, get an AM2+ board. Just make sure the manufacturer offers BIOS updates to support new CPU's if you have the intention of eventually upgrading to a Phenom (AM3 CPU's have DDR2 controllers on the die as well as DDR3 controllers, so they will work in AM2+ boards if the BIOS supports them). AMD should be making AM3 CPU's well into 2012, so you should have plenty of time to upgrade your CPU (should you need to) before the apocalypse ;) .

EDIT: BTW, installing a stock AM2 cooler is not hard if you really follow the diagram and make sure the lever is parallel to the board when trying to attach the second clip. Otherwise, it IS a pain. It took me a couple times to learn this.

---

### Post by Nick_Jinn on 2010-06-30
I think I might want to go bare bones and get a Phenom Quad out of the box. I think I will reserve my computer building practice to old used hardware. 

 I need links to the best deals on bare bones though. I could go for AM3 if they have a really good deal on 2x 2gb DDR3 Ram.

---

### Post by VeeDubb on 2010-06-30
> **Nick_Jinn said:**
> Yeah? What motherboard is it? Its not the Foxconn is it? I heard rumors that they sabotaged the bios to not support aspects of linux....I dont know if its credible though.

go here->  [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600007943+600008723&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=770](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007625+600007943+600008723&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=22&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=770)

If you sort by lowest price, the first three hits all cost the same ammount, all have the same features as far as CPU/RAM/PCI slots.  You can chose from Biostar, Asrock and ECS.  I've used adrock and ECS boards with linux without issue.  Never tried biostar.

The grab this CPU -> [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103656](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103656)

And then grab this RAM -> [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231253](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231253)

The total cost is $272.98 + shipping.

You get your 3 PCI slots, a quad core, 4GB of dual chanel memory, and lots of future upgradability.

If you decide you want USB3.0, you can grab the $74.99 ASROCK a few places down the list, and only increase your total cost by $15.00

---

### Post by VeeDubb on 2010-06-30
Oh, and I really wouldn't go with a barebones in your situation.  You'll end up paying for a lot of components you've already got, and having to buy a lot of the same stuff anyway.

Barebones are a great way to quickly build a new system, but they're rarely worth the trouble or money when rebuiling an existing system.

---

### Post by Nick_Jinn on 2010-07-01
I do sort of want a new case. I dont want to be limited to micro motherboards. I have one larger space case, but its missing a few cords for sound plug ins....not very expensive to replace, but a pain in the ***, and its also not as pretty or well organized compared to some other cases.

So I either need to buy a new case and hope I dont do something stupid when I try to assemble everything, or if I go for the AM2+ I can get a 3.4 ghrz Quad Phenom black edition, use 4gb of RAM that I already have, and use the rest of my components.

I might be able to do it a little cheaper if I build it myself and might get a little nicer case, but my confidence in my ability to build computers is slightly shaken after ruining my crappy acer mobo by superglueing the cooler mount after losing the screws. 

I hear AM3 theoretically supports DDR2, but the slots fit differently....so how does that work? I buy an adapter?


The case is an added expense I have to consider. I also probably am going to need a stronger power supply.

---

### Post by Nick_Jinn on 2010-07-01
So Im about ready to do this, one of two ways.


So could somebody explain to me why in a year or two I wont be able to put a Phenom II in an AM2+ board? If I already have the board are they going to stop being compatible?

If AM2+ is going to be a thing of the past, it seems like upgrading the board wont be a major expense in a few years. I can still keep the CPU, video card, PCI cards and hard drives and optical drive. Its a small waste but I get to save $100 on RAM in the short term. 4gb seems sufficient if I run linux instead of windows.

USB3 is nice, but I can get a firewire card in the meantime.

For $400 I can get a 3.4 ghrz phenom sent to my house with a case, fans, cooler, firewire, up to date card reader, and 550 power supply.

Down the road I could swap out the motherboard for another $70, but I get to save $100 on RAM until that happens. 

I am thinking about getting it from Ascendtech.



Then again, Im tempted to see if I can build one myself. I might get a nicer case if I pick it out myself. RAM wont be as good of a deal if I dont buy with a kit, but its still in range, and I would probably have to use the chip I already have to stay in budget after buying 4gb of RAM, but I would have a totally decent AM3 and be able to upgrade the chip instead of the motherboard later.



Even if I end up doing something different I would like to thank everyone for offering so much valuable knowledge and insight.

---

### Post by VeeDubb on 2010-07-01
> **Nick_Jinn said:**
> For $400 I can get a 3.4 ghrz phenom sent to my house with a case, fans, cooler, firewire, up to date card reader, and 550 power supply.


Well, I guess I've made my opinion clear, but I love thes discussions so I'll give it one more time.

I would not buy a barebones in your situation.  They are rarely if ever a good deal. 

You could get a comparable case with a 480w power supply (more than enough unless you're running dual video cards or 6 hard drives) for $29.99 at the same site I listed already, Pay $15 more for the board with USB 3.0 which is better than firewire, add a card reader for a 3.5" slot for no more than $20, and how you've got everything that barebone would give you, a better quality motherboard, more current RAM and you're still spending $60 less than the barebones system.


I think what might help you for perspective sake, would be to see when I WOULD go with a barebone system:

a. You're completely intimidated by the prospect of building a system, but want a better deal than going to Dell.  

b. You're not concerned about getting the "best" deal, but you want reasonably cheap, and you're in a hurry.  

c. You're looking for a compromise between material cost and labor cost when building several machines.

d. You're building something specialized where using a barebone system gives you options that you can't get doing it all yourself.  For example, building and Atom/IO based home theater.  You can USE one of the zbox barebone systems by zotac, or build your own.  However, the case used for the zbox is much slimer than anything you coule buy from a 3rd party, making it a worthwhile option.




2 quick side notes:  

CPU speed - For the most part, there is no real world performance difference a quad core Phenom at 2.8ghz and a quad core phenom at 3.2.  CPU speed stopped being a primary factor in performance a long time ago.

RAM - Now, as far as DDR2/DDR3 and adapters, I think the confusion there started with bad info from me, so let me clear it up.

Any chipset that can support and AM3 CPU, can technically support DDR2 or DDR3 memory,  and the CPU's know how to deal with both kinds as well.  However, each motherboard will be set up to use one or the other, and there is absolutely no way to "adapt" between the two.  You make tha choice when you buy your motherboard.  End of story.

---

### Post by cascade9 on 2010-07-01
Delete

---

### Post by cascade9 on 2010-07-01
Gah, triple post! somebody delete this...pelase.

---

### Post by cascade9 on 2010-07-01
Delete me as well! 

Stupid 'database error' :|

---

### Post by cascade9 on 2010-07-01
> **Temüjin said:**
> If you have DDR2 and a nice AM2 CPU already, get an AM2+ board. Just make sure the manufacturer offers BIOS updates to support new CPU's if you have the intention of eventually upgrading to a Phenom (AM3 CPU's have DDR2 controllers on the die as well as DDR3 controllers, so they will work in AM2+ boards if the BIOS supports them). AMD should be making AM3 CPU's well into 2012, so you should have plenty of time to upgrade your CPU (should you need to) before the apocalypse ;) .
   
   EDIT: BTW, installing a stock AM2 cooler is not hard if you really follow the diagram and make sure the lever is parallel to the board when trying to attach the second clip. Otherwise, it IS a pain. It took me a couple times to learn this.
   
   This is probably what  would do. 
   
   I'd proably also go for a microATX board, and shove it in the acer case (provided that it has the mount hole patern for standard microATX motehrboards). 
   
   That way, later on, you can buy a whole new boxxen, rip out everything but the smallest HDD from the acer, and then sell it.
   
   You can get a microATX case for not that much (and even lower if yuo get anj openbox deal)-
   
   [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131608R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131608R)
   
  > **Nick_Jinn said:**
> I think I might want to go bare bones and get a Phenom Quad out of the box. I think I will reserve my computer building practice to old used hardware. 
  
  
Understandable. I wouldnt, but I agree 100000% with VeeDubb ("I would not buy a barebones in your situation. They are rarely if ever a good deal.")

> **Nick_Jinn said:**
> So could somebody explain to me why in a year or two I wont be able to put a Phenom II in an AM2+ board? If I already have the board are they going to stop being compatible?

They probably wont stop being compatible, and I havent checked AMDs roadmaps, but its always possible that AMD will put out Phenom IIs with no DDR2 controller (and call it AM3+ or something). I guess that at some point the DDR2 controller will be removed, its only a question of when. 

Also, at some point the new 'magny cours' opteron CPUs will filter down to the desktop, in the same way that the X6 has already (X6 was avaible for a long time as a server chip). 8/12cores on teh desktop....and I wouldnt be suprised if they are ''true" AM3 (DDR3) only, or become AM3+ CPUs. 

> **Nick_Jinn said:**
> If AM2+ is going to be a thing of the past, it seems like upgrading the board wont be a major expense in a few years. I can still keep the CPU, video card, PCI cards and hard drives and optical drive. Its a small waste but I get to save $100 on RAM in the short term. 4gb seems sufficient if I run linux instead of windows.

4GB 'sufficient'? LOL, I run 2GB on my main desktop, and its more than fine, and I've got a few machines that have far, far less (down to 256MB on my media box, whcih runs fine with some linux distros) 

Dont forget that in a few years, whatever video card you have now will be blown away by cheap lowend card (that always happens), the newer HDDs avaible then will be faster (and much, much faster when you think about SSDs). You optical drive is IDE I guess, and IDE is gradually being deleted- its already possible to get motherboards with no IDE, and sooner or later IDE will be a 'feature' you will have to pay extra for. 

> **Nick_Jinn said:**
> USB3 is nice, but I can get a firewire card in the meantime.

Which is fine if you have USB/Firewire devices. 

> **Nick_Jinn said:**
> For $400 I can get a 3.4 ghrz phenom sent to my house with a case, fans, cooler, firewire, up to date card reader, and 550 power supply.

Down the road I could swap out the motherboard for another $70, but I get to save $100 on RAM until that happens. 

I am thinking about getting it from Ascendtech.

550watts.....umm, well, to be honest, there are 550watt power supplies ('generic' or worse yet 'yum cha'), and 550watts power supplies (good brand). I'd take a good brand 400/430 over a generic 550 anyday ;) 

I didnt find the barebones systems there, but I did look at the sysmtem builder. No AM3 boards listed, and what part could choose were a fair chunk more expensive than newegg. Eg- 

[Amd Phenom Ii X2 550 3.1ghz Processor]("http://javascript%3Cb%3E%3C/b%3E:printitem%28%27CP64AM2PIIX2550#119.95#1#T#119.95%27%29")                                                                                                                                                                                   [COLOR=brown]                                                              [Add $119.95] [/COLOR]
[Amd Phenom Ii X4 965 3.4ghz Processor]("http://javascript%3Cb%3E%3C/b%3E:printitem%28%27CP64AM2PIIX4965#204.95#1#T#204.95%27%29")                                                                                                                                                                                   [COLOR=brown]                                                              [Add $204.95] 
[/COLOR][Amd Phenom Ii X6 1090t 3.2ghz Processor]("http://javascript%3Cb%3E%3C/b%3E:printitem%28%27CP64AM3PX61090T#399.95#1#T#399.95%27%29")                                                                                                                                                                                   [COLOR=brown]                                                              [Add $399.95] [/COLOR]

[http://www.ascendtech.us/customkititems.asp?kc=DTA64AM2CSTCNFG](http://www.ascendtech.us/customkititems.asp?kc=DTA64AM2CSTCNFG)

The same CPUs at newegg are 
X2 555- $101
X4 965- $180
X6 1090t- $296 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007671%2050001028&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007671%2050001028&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=100)

The better the part, the more they are charging. Not just on CPUs, its everything. If you are after a very bottom end system, they would be OK..... 

> **Nick_Jinn said:**
> Then again, Im tempted to see if I can build one myself. I might get a nicer case if I pick it out myself. RAM wont be as good of a deal if I dont buy with a kit, but its still in range, and I would probably have to use the chip I already have to stay in budget after buying 4gb of RAM, but I would have a totally decent AM3 and be able to upgrade the chip instead of the motherboard later.

Might I direct you to ibuypower-

[http://www.ibuypower.com/](http://www.ibuypower.com/)

Still not as cheap as buying and building yourself, but they do have a much nicer range of parts avaible, and the price difference between there and newegg is much lower. 

You cant spec a 'barebones' system there that I've seen, but you can always try sending them an email or calling them. 

> **Nick_Jinn said:**
> Even if I end up doing something different I would like to thank everyone for offering so much valuable knowledge and insight.

No problem. I wont speak for anybody else posting here, but I admit to being a hardware drooler :biggrin:

---

### Post by Yellow Pasque on 2010-07-01
Nvm

---

### Post by Yellow Pasque on 2010-07-01
Here we go: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138168](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138168)
Better yet (since it supports 140W CPU's): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131618](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131618)

---

### Post by Nick_Jinn on 2010-07-01
Ibuy power is an awesome deal from what it looks like. 

I thought about buying a microATX and shoving it in there, but I would hate for it to arrive and have it not fit. I am in a bit of a hurry. I think I will just keep my eyes out for a used product from a broken system and sell it when I have the time.

Does this sound like an ok system?


ECS GF8200A PHENOM-2 X4 QUAD CORE MBOARD 														
AMD PHENOM II X4 965 3.4GHz PROCESSOR 														
 														HIGH SPEED - HEAVY DUTY QUIET RUN COOLER   														(Generic?)
ARCTIC SILVER 5 3.5GRAM THERMAL COMPOUND
FLASH MEMORY CARD READER ALL-IN-1 DRIVE 														
ATX window case
650Watt Dual Core / Quad Core Certified  														(Generic?)
Case Cooling Fan 80mm (Regular Speed)  (generic)
Florescent light (green).

+ my
NVidia Geforce 6800
4gb DDR2 RAM
DL DVD Burner
Sound Card
other odds and ends.



Honestly I am a little intimidated of building it myself after toasting my Acer with superglue. I bet I could do it right the second time if no screws are missing, but I am just slightly intimidated.

I got the above specs for $360. Is that a bad deal? Its not too late to cancel it, but it would need to save me $50 or more to be worth it, without any decrease in specs.

---

### Post by Nick_Jinn on 2010-07-01
I tried ordering the same parts I needed from Newegg individually, only using a better quality power supply, motherboard and a nicer case, and it ended up being almost $40 more expensive.

Ascendtech seems to have some really good prices, and it comes preconfigured.


Am I really going to like it that much more if I build it myself from good parts?



I am tempted to go for the package deal all set up for me.

---

### Post by Nick_Jinn on 2010-07-01
So if I build this myself instead, am I going to have to set up the bios myself or do I just plug and play? Setting up the bios is a little beyond my current skill level, and I would rather practice on junk parts before trying it on my primary hardware.

---

### Post by VeeDubb on 2010-07-01
The reality is that we're WELL outside the realm of black and white fact at this point.

Pricing out from newegg with better part is $40 more, but that's for better parts.  Buy comparable generic parts and it will probably be $40 less.

Of course, you can frequently get by very successfully with generic parts.  I've done it plenty of times.  The power supply in my high-end cooler master case is the generic power supply that came with it, and it's been in there through 3 motherboards.  (you REALLY don't need a 680watt power supply)

You've got it down to where you have multiple options in similar price ranges, with marginal differences.

Will you notice a big difference building your own?  A big part of the answer to that is you. 

Will YOU feel better building your own?  There's no wrong answer to that question.

And what about the generic parts?  Well, my experience tells me that as long as they have the features you want, the biggest difference is the odds you'll have to return them due to defects.  Good brands tend to have better quality control, but 8 or 9 times out of 10, generic parts come through just fine.  Is an 80-90% chance of getting a good part an acceptable risk to you, or would you be more comfortable with a 95-99% chance of getting a working part?   Again, there's no wrong answer.

You've also said you're a bit intimidated after the super-glue fiaso.  Once again you're faced with the choice of avoiding the same problem, or going further and building your own to prove you can do it.  Again, there's no wrong answers.

You've got multiple great options, so it's just a matter of picking the one in your price range that best meets your needs and wants.

---

### Post by VeeDubb on 2010-07-01
> **Nick_Jinn said:**
> So if I build this myself instead, am I going to have to set up the bios myself or do I just plug and play? Setting up the bios is a little beyond my current skill level, and I would rather practice on junk parts before trying it on my primary hardware.

The answer to that is the same regardless of whether you buy a barebones system or build from scratch.  The default settings in the bios work perfectly for 95% of people, but sometimes require minor tweaking.  This is not an issue to be concerned aobut.

---

### Post by Nick_Jinn on 2010-07-02
Yeah, I think I will be ok, but only because I have people like you who enjoy helping people like me. The best advice I have gotten has come from the Ubuntu forums.


I appreciate everyones help.


And I learned something today....Dont buy from Ascendtech unless you know what you are doing. They tried to sell me a 95 wat motherboard that didnt support the 140 wat phenom chip they were selling me, and yet there they both were as the default for that model.

Just horrible. 24 hours later they didnt even process my order. I would have waited until next week probably just for them to tell me that my order couldnt be processed and I had to give them more money to upgrade.... Or worse, they just hope that it can withstand it and send it to me as is. That and apparently they use refurbished parts without telling you with only 90 days warranty. Hardly worth the discounted price. Maybe it works out for some people, but you had better pay attention to whether the chip is support by the motherboard, because many of their default combinations are incompatible.

So I decided to build this myself. 


If I get stuck you know where I will be.

---

