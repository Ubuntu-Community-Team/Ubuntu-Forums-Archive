---
title: "How to know if Dual Channel RAM working?"
date: 2010-07-15
forum: Hardware
---

### Post by onecallednick on 2010-07-15
[IMG]http://lh6.ggpht.com/_mrjNojZM9b8/TD9M2vColMI/AAAAAAAAFoU/ftsAK9jVxPw/s640/Catalyst.png[/IMG]Hi,  I just built myself a nice modern system to run GNU+Linux on.  It's an AMD AM3 board, and I put 2 x 2GB DDR3-1066 on it.  
     The thing is when I go into the Catalyst Control Center, click information, and look at "memory type", it says I have DDR2-533, exactly half the bandwidth of my RAM.  I wonder if this means my RAM isn't operating in dual channel mode?  I've heard they have to have the exact same chips to work properly, and though they are the same brand and model, I got them at different times from different places.
     Is there any way to test and see if dual channel is working on Ubuntu?  I've googled it and come up dry.
My system in case it helps:
Biostar A785G3 Ver 6.x AM3 Motherboard w/ integrated Radeon HD 4200 GPU
2 x 2gb DDR3-1333 Kingston Value RAM
AMD Sempron 140 2.7Ghz single core

---

### Post by cj.surrusco on 2010-07-15
DDR stands for Double Data Rate. Therefore, it is actually running at twice the speed of 533mhz, which is right where you want it to be, at 1066mhz.

---

### Post by AltomineUK on 2010-07-15
Dual Channel's a motherboard technology, so if your motherboard supports it you've got it. I checked your motherboard specs and it confirms you have dual channel support. Dual Channelling does not apply to the RAM modules or your graphics chipset. Catalyst control centre shows the setting of your ATi card, not your RAM, so it won't tell you much about any dual channels.

Check your BIOS. It's all in there.....

---

### Post by endotherm on 2010-07-15
the only time I have ever seen confirmation about ram channel duplexing or ganging is in the bios load screen. I don't think there are any apps that show that for any platform I am aware of, but check lshw-gtk and see if it tells you.

---

### Post by onecallednick on 2010-07-15
Using lshw I get this:[IMG]http://lh3.ggpht.com/_mrjNojZM9b8/TD9d5mnp9sI/AAAAAAAAFoc/oXozY99pIoU/s640/Screenshot.png[/IMG]
So I still don't know, but I guess I also have no indication that it's not working, as far as I can tell.  Checked through the bios and didn't see anything explicitly stating "ram in dual channel mode," would it use less familiar lingo?

---

### Post by endotherm on 2010-07-15
well i only see it as a status message at the very beginning of boot. it just kind of flashes by while the post is enumerating cpu and the the hdds. 

my guess is that it is on if correctly installed. dualchannel has always been a very "behind-the-scenes" setting.

---

### Post by AltomineUK on 2010-07-15
> **AltomineUK said:**
> Dual Channel's a motherboard technology, so if your motherboard supports it you've got it. I checked your motherboard specs and it confirms you have dual channel support. Dual Channelling does not apply to the RAM modules or your graphics chipset. Catalyst control centre shows the setting of your ATi card, not your RAM, so it won't tell you much about any dual channels.

Check your BIOS. It's all in there.....

I meant check inside BIOS....

---

### Post by onecallednick on 2010-07-15
Here's the settings I've found in the mobo bios manual:


DCT Unganged Mode
This item controls the DRAM controller ganged (128bit*1) / unganged (64bit*2)
dual-chann el operation mode. If two DRAM modules with different size are
installed, using unganged mode can still make it run in dual-channel operation.
Options: Always (Default) / Auto

I set this to auto since I have identical DIMMs.

Channel Interleaving
T his item allows you to control the DDR2 dual-channel function.
Options: XOR of Address bits [20:16, 6] (Default) / XOR of Address bits
[20:16, 9] / Address bits 6 / Address bits 12 / Disabled

Bank Interleaving
Bank Interleaving is an advanced chipset technique used to improve memory
perform ance. Memory interleaving increases bandwidth by allowing simultaneous
access to more than one piece of memory.
Options: Auto (Default)

So, I should be good, right?  Thanks, this has been really educational.

---

### Post by AltomineUK on 2010-07-16
Yes, it should be good. Enjoy the wonders of Dual Channels.

---

### Post by cascade9 on 2010-07-16
> **onecallednick said:**
> Using lshw I get this:

So I still don't know, but I guess I also have no indication that it's not working, as far as I can tell.  Checked through the bios and didn't see anything explicitly stating "ram in dual channel mode," would it use less familiar lingo?

Well, thats a new one, I didnt know that lshw has a GUI. 

If lshw-gtk runs the same as the version of lshw I've got installed, you may well be running at 1/2 speed. My (CLI) readout is like this- 

```
*-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 1800 MHz (0.6 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 1800MHz (0.6ns)
        *-bank:1
             description: DIMM 1800 MHz (0.6 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 1800MHz (0.6ns)
```

It might be that you have an different version of lshw that reports timing differently.....

BTW, if you have DDR3 1333 why are you running it at 1066/533 anyway?

---

### Post by onecallednick on 2010-07-16
I'm not any more.  Just upgraded to an Athlon II X4 635, but I was using a Sempron 140 which only has a 1066 memory controller.
Wierd!  Check this out:

 *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 200 MHz (5.0 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 200MHz (5.0ns)

What the heck is going on?

---

### Post by cascade9 on 2010-07-17
Thats bad. 

Either your RAM has underclocked itself for some reason, or your have a dodgy RAM stick. I'd try running memtest86

---

### Post by onecallednick on 2010-07-17
I set it back to unganged mode and now both sticks are recognized as 667 Mhz.  Which is right, becuase they operate at 1333 MegaTransits/S not Megahertz.  According to wikipedia at least.  I will run memtest86 when i get a chance and post results.

---

### Post by AltomineUK on 2010-07-17
> **onecallednick said:**
> I set it back to unganged mode and now both sticks are recognized as 667 Mhz.  Which is right, becuase they operate at 1333 MegaTransits/S not Megahertz.  According to wikipedia at least.  I will run memtest86 when i get a chance and post results.

Please leave it running in Ganged Mode. In Unganged mode, the memory controller only allows asynchronous access of data from your RAM module and hence will not function in dual channel. That is if you want dual channel...... and please don't worry of your memory clock speeds. The memory controller will adjust this to match an optimum level as both memory modules would work 'together' in ganged mode..

---

### Post by AltomineUK on 2010-07-17
> **cascade9 said:**
> Thats bad. 

Either your RAM has underclocked itself for some reason, or your have a dodgy RAM stick. I'd try running memtest86

No, it's not bad.....and no, he RAM module is not dodgy....

---

### Post by onecallednick on 2010-07-17
boy, there sure are a lot of opinions on this topic!  I'm keeping it in unganged mode for now because if I don't one registers as 667 mhz and the other registers as 200 mhz.  The BIOS manual states this is still dual channel, just 2X64 bit channels instead of 1X128 bit channel.

---

### Post by AltomineUK on 2010-07-18
> **onecallednick said:**
> I'm keeping it in unganged mode for now because if I don't one registers as 667 mhz and the other registers as 200 mhz.  The BIOS manual states this is still dual channel, just 2X64 bit channels instead of 1X128 bit channel.

Ok..... as you wish. 

Yes, 1X128 is the higher bandwidth channel (Ganged) and both memory modules will work TOGETHER. 2X64 (Unganged, where both RAM DIMMs work separately according to their own clocks) only allow the AMD to access each memory stick individually (which permits queuing of data before it can be accessed). This is why, in Ganged, you get one clock speed lesser than the other and in Unganged, both work at independant speeds rate. Unganged is useful if you have two sticks of different memory sizes, however, if you are happy leaving it in unganged mode that's completely FINE.

> **onecallednick said:**
> boy, there sure are a lot of opinions on  this topic!
It is as they say: Gaining Knowledge Leads Towards Wisdom....but Sharing Knowledge Leads Towards Community.

Peace.

---

### Post by cascade9 on 2010-07-18
> **AltomineUK said:**
> No, it's not bad.....and no, he RAM module is not dodgy....

What, 1 stick @ 667 and 1 stick at 200 isnt bad? o.O You've got to be kidding. 

> **onecallednick said:**
> I set it back to unganged mode and now both sticks are recognized as 667 Mhz. Which is right, becuase they operate at 1333 MegaTransits/S not Megahertz. According to wikipedia at least. I will run memtest86 when i get a chance and post results.

Yes, all DDR 'lies' about the speed, its really half of the reported speed. But all the versions of lshw I've seen report the 'lie' speed, not the real speed, so I still think you've got an issue (just tried it with linux mint 8 and I got the same 1800MHz as I got on a much later version of lshw). 

Its possible that your RAM has problems running in 'ganged' mode and that is why you had 1 stick @ 667 and 1 stick @ 200. Something is definitely dodgy, if that is the RAM, the RAM controller or lshw making a horrible mistake, I dont know......I doubt its lshw though. 

What motherboard and RAM are you using?

---

### Post by AltomineUK on 2010-07-18
> **cascade9 said:**
> What, 1 stick @ 667 and 1 stick at 200 isnt bad? o.O You've got to be  kidding.

I have fully explained the reasons -__- ....That's how they are DESIGNED to work in Ganged mode.

I'll explain again, if both DIMMs worked according to their maximum internal clock-rate in ganged mode, it will result in a lot of contention as they are sharing the same bus. The bus itself has a bandwidth limit. When contention occurs, individual data bits will collide and end up carrying null data. So to avoid this both will run at different clockrates to help with things like multiplexing and avoid data collisions. THIS ONLY HAPPENS IN GANGED MODE.

---

### Post by cascade9 on 2010-07-18
> **AltomineUK said:**
> I have fully explained the reasons -__- ....That's how they are DESIGNED to work in Ganged mode.

No, they are designed to work in either mode at the rated speed. Not 1 at 667MHz, 1 at 200MHz. 

Its still wrong, ganged or unganged I still get 1800MHz from both sticks from my lshw output.

---

### Post by cascade9 on 2010-07-18
> **AltomineUK said:**
> I'll explain again, if both DIMMs worked according to their maximum internal clock-rate in ganged mode, it will result in a lot of contention as they are sharing the same bus. The bus itself has a bandwidth limit. When contention occurs, individual data bits will collide and end up carrying null data. So to avoid this both will run at different clockrates to help with things like multiplexing and avoid data collisions. THIS ONLY HAPPENS IN GANGED MODE.

That doesnt happen here, with older or newer versions of lshw, ganged or unganged. 

I think your wrong. If you've got a link, maybe I would believe you.

---

### Post by AltomineUK on 2010-07-18
Have fun :D

READ HERE!!!! 
[http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/1](http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/1)

[http://en.wikipedia.org/wiki/Interleaving](http://en.wikipedia.org/wiki/Interleaving)

---

### Post by cascade9 on 2010-07-18
I'll take that as a "I have no links, I was just hoping that was true". 

Not the first time you've posted complete tosh, like "old PC's (9-10 years old) all have AGP as well PCI" or "although if you want to unlock two extra cores you have to go for its bigger brother..... 555 Black Edition.".

---

### Post by AltomineUK on 2010-07-18
> **cascade9 said:**
> I'll take that as a "I have no links, I was just hoping that was true". 

Not the first time you've posted complete tosh, like "old PC's (9-10 years old) all have AGP as well PCI" or "although if you want to unlock two extra cores you have to go for its bigger brother..... 555 Black Edition.".

Please don't be rude...... I keep asking you to read posts properly before posting remarks.... If you lack some manners please go learn some. If you want to discuss about something else, start a post.... I still stand by all the things I have said. 

If you want to post comments aimed at insulting each other's intellect please do it somewhere appropriate. Forums nowadays have far too many such comments.....This is not the place...

---

### Post by cascade9 on 2010-07-18
> **AltomineUK said:**
> Please don't be rude...... I keep asking you to read posts properly before posting remarks.... I hope YOU do know what you are talking about. If you lack some manners please go learn some.

Your seem to be making 2 mistakes- 

1- I dont read your posts (not true)
2- Reading your posts = agreement with you (not true either) 

I read what you said, I disagree. 

I can post my lshw output if you really want, ganged, unganged, and from various different lshw versions.....have you got any eivdence at all that you are right? 

If so, please post it. 

BTW, if 'tosh' is insulting to you, then dont post things that are completly, totally and proveably wrong.

Edit- 

> **AltomineUK said:**
> Have fun :D

READ HERE!!!! (intended for a certain person who keeps missing things...)

[http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/1](http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/1)

[http://en.wikipedia.org/wiki/Interleaving](http://en.wikipedia.org/wiki/Interleaving)

Original post 38minutes ago, edited 8 minutes ago. So its not like I'm missing anything, you just edit your posts after things have moved on....

As for those links, they have nothing in them that I didnt already know. Just in case you missed though- 

> Because the two modules are accessed at the same time, they must be identical (same capacity, same timings and same clock rate).

[http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/2](http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/2)

Yes, I agree with that....

You've given no link explaining why in 'ganged' mode onecallednick had 667/200 RAM (which according to that hardware secrets page means 'no dual channel') then in 'unganged' mode it went back up to 667/667 RAM (which is wrong anyway, barring some odd hardware or the lshw version).

---

### Post by AltomineUK on 2010-07-18
> **cascade9 said:**
> Your seem to be making 2 mistakes- 

1- I dont read your posts (not true)
2- Reading your posts = agreement with you (not true either) 

I read what you said, I disagree. 

I can post my lshw output if you really want, ganged, unganged, and from various different lshw versions.....have you got any eivdence at all that you are right? 

If so, please post it. 

BTW, if 'tosh' is insulting to you, then dont post things that are completly, totally and proveably wrong.

Edit- 



Original post 38minutes ago, edited 8 minutes ago. So its not like I'm missing anything, you just edit your posts after things have moved on....

As for those links, they have nothing in them that I didnt already know. Just in case you missed though- 



[http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/2](http://www.hardwaresecrets.com/article/Everything-You-Need-to-Know-About-Dual-Channel/133/2)

Yes, I agree with that....

You've given no link explaining why in 'ganged' mode onecallednick had 667/200 RAM (which according to that hardware secrets page means 'no dual channel') then in 'unganged' mode it went back up to 667/667 RAM (which is wrong anyway, barring some odd hardware or the lshw version).

It has to be interleaved for both to work at same clock speed. The wikipedia link states that..... as for edits I realised i forgot to make the paste bit (my bad)...copied but no paste hence "Have Fun...then blank..." Check BIOS for interleaving.

I think we have got more than enough info here, so I'll be a bit more conservative. Are you sure you have read everything completely. You will know about the Ganged bits it you read the links COMPLETELY.

---

