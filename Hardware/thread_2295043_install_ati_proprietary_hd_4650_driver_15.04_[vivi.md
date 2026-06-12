---
title: "install ati proprietary hd 4650 driver 15.04 [vivid]"
date: 2015-09-15
forum: Hardware
---

### Post by pooldemon6000 on 2015-09-15
i've been trying to install the legacy driver, 13.12 and have also tried 12.6.

13.12 there are no specifications listed, but i am directed by the ati site to that driver and i get the error no supported hardware or w/e.
12.6 seems to install with an error regarding firegl, i think it has to do with my kernel version being the latest stable ubuntu is comfortable with since i also saw a strange output about it.

i've followed a guide to reinstall the previous driver settings, so not sure if the log files survived, but once i rebooted i got the error that xserver couldn't load a .so driver that was present in the directory given in the error.

my card is not listed in the 15.7 package, am i just boned?

the updated mesa driver i found in some ppa works a lot better when gaming than the defaults, but there is some graphical jitter with other players present (medal of honor allied assault) and i cannot install steam using it, if anyone can help get this sorted properly, it would be very much appreciated.

additional proprietary driver application doesn't list my card
if i install from the .run, i can apt-get update and then apt-get upgrade using 13.12, but i didn't try that with 12.6.

---

### Post by QIII on 2015-09-15
Hello!

AMD dropped proprietary driver support for Linux for all adapters prior to HD 5000 series.

There is no proprietary driver that will work for that card.  The open source driver that was installed with Ubuntu is the only choice.  That is why you see the "No supported device" message.

---

### Post by pooldemon6000 on 2015-09-17
> **QIII said:**
> Hello!  AMD dropped proprietary driver support for Linux for all adapters prior to HD 5000 series.  There is no proprietary driver that will work for that card.  The open source driver that was installed with Ubuntu is the only choice.  That is why you see the "No supported device" message.  i believe you when you say that, but i'm confused as to why i was directed to the 13.1 installer on the ati website, what about older versions, i have seen in other forum posts that people had been using 12.6 for the 4650.

---

### Post by Yellow Pasque on 2015-09-17
13.1 was just a minor update (some Steam fixes) to the 12.6 Legacy driver. At any rate, neither one is going to work on any version of Ubuntu later than 12.04.1.
Were you having issue(s) with the default open source driver or did you just assume that you needed a proprietary driver?

---

### Post by pooldemon6000 on 2015-09-18
> **Temüjin said:**
> 13.1 was just a minor update (some Steam fixes) to the 12.6 Legacy driver. At any rate, neither one is going to work on any version of Ubuntu later than 12.04.1.
Were you having issue(s) with the default open source driver or did you just assume that you needed a proprietary driver?

i am having minor issues with a game, it isn't unplayable, but there is some video jitter, not full lag, but enough to make playing not as enjoyable and i can't install steam without the driver, if i downgrade to 12.04.1 i won't have repo access i'm sure...

guess maybe i need to save up for a new card, maybe nvidia has been better to the linux community, second time ati boned me on drivers completely.

i wonder if i could do something like with arch or an old wrapper script using old gtk libs, just install what it needs to run?

---

### Post by Bashing-om on 2015-09-18
pooldemon6000; Hello;

Just food for thought:
> 
, if i downgrade to 12.04.1 i won't have repo access i'm sure...

Oh contrar ; Release 12.04.[color=green]1[/color] has full support 'til April of 2017. Possible that with 12.04.1 you will be able to install the legacy proprietary graphics driver.

[INDENT][INDENT]just my 1 pounds worth
[/INDENT][/INDENT]

---

### Post by pooldemon6000 on 2015-09-19
> **Bashing-om said:**
> pooldemon6000; Hello;

Just food for thought:

Oh contrar ; Release 12.04.[COLOR=green]1[/COLOR] has full support 'til April of 2017. Possible that with 12.04.1 you will be able to install the legacy proprietary graphics driver.
[INDENT][INDENT]just my 1 pounds worth
[/INDENT]
[/INDENT]


interesting, i had forgotten that.

after i get the driver installed will taking updates affect the driver or more importantly could i sudo apt-get upgrade and be on 15.04, or would upgrading the kernel alone break everything?

not that i even know how to upgrade the kernel (yet).

---

### Post by Bashing-om on 2015-09-19
pooldemon6000; Well;

Like this; release .1 of 12.04 has that older kernel and Xstack that has the support for the FGLRX driver. So long as you do not opt in for HWE you will remain on that structure; the updates on the .1 release will remain supporting that series of the kernel - even when you are fully updated/upgraded ( 12.04.5 ?) . When you upgrade beyond 12.04.1 base structure then all those support libraries are changed and no longer work with the needed kernel version. That does mean that 15.04 will not support that older hardware - except open source drivers. Open source drivers are your only option.

IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. Terminal command -> X -version to determine the x-server version.

I too fall into that category of no OEM support for my ATI driver. However, for my needs the open source driver functions well .

The only long term solution - if one requires a proprietary graphic's driver - is to upgrade the hardware.

That is the way it is
[INDENT][INDENT][INDENT]ever changing technology
[/INDENT][/INDENT][/INDENT]

---

### Post by pooldemon6000 on 2015-09-21
> **Bashing-om said:**
> pooldemon6000; Well;

Like this; release .1 of 12.04 has that older kernel and Xstack that has the support for the FGLRX driver. So long as you do not opt in for HWE you will remain on that structure; the updates on the .1 release will remain supporting that series of the kernel - even when you are fully updated/upgraded ( 12.04.5 ?) . When you upgrade beyond 12.04.1 base structure then all those support libraries are changed and no longer work with the needed kernel version. That does mean that 15.04 will not support that older hardware - except open source drivers. Open source drivers are your only option.

IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. Terminal command -> X -version to determine the x-server version.

I too fall into that category of no OEM support for my ATI driver. However, for my needs the open source driver functions well .

The only long term solution - if one requires a proprietary graphic's driver - is to upgrade the hardware.

That is the way it is[INDENT][INDENT][INDENT]ever changing technology
[/INDENT]
[/INDENT]
[/INDENT]


i had a idea to use a wrapper like ndiswrapper does for wireless drivers, but couldn't find anything about it having been done.
thanks for helping

---

### Post by mastablasta on 2015-09-21
you can however upgrade the opensource drivers. there are one or two descent PPA's for that. see if that solves the issue. if not then I am interested in the old card if you are from EU :P

---

### Post by pooldemon6000 on 2015-09-23
> **mastablasta said:**
> you can however upgrade the opensource drivers. there are one or two descent PPA's for that. see if that solves the issue. if not then I am interested in the old card if you are from EU :P

i've tried one ppa i found,  deb [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) vivid main, it helped a little, but could be a lot better.

if i had one to replace it with i would gladly arrange something with you, i am in U.S.

---

### Post by mastablasta on 2015-09-24
xorg edgers is another testing one: [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

also check if you can find any parameters you can use below the table: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/) 

as you can see not all features of r700 chip are enabled. AMD helped a bit but I am not sure if they will continue to help the opensource driver or if there is actually any movement for these a bit older models. in any case dont' expect "windows drivers performance". 

I have ATI 9600 - in windows it easily ran Morrowind and such in Linux it is overheating, struggling with any QIII engine game (overheating mostly). this is one of the reasons why I keep the PC with radeon 3650 loaded with WinXP. performance in Linux got better but is still not the same as on XP.

---

### Post by pooldemon6000 on 2015-09-26
> **mastablasta said:**
> xorg edgers is another testing one: [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

also check if you can find any parameters you can use below the table: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/) 

as you can see not all features of r700 chip are enabled. AMD helped a bit but I am not sure if they will continue to help the opensource driver or if there is actually any movement for these a bit older models. in any case dont' expect "windows drivers performance". 

I have ATI 9600 - in windows it easily ran Morrowind and such in Linux it is overheating, struggling with any QIII engine game (overheating mostly). this is one of the reasons why I keep the PC with radeon 3650 loaded with WinXP. performance in Linux got better but is still not the same as on XP.

well i just went and bought a EVGA GTX 660 SuperClocked 2GB GDDR5 PCI Express 3.0 x16 HDCP Ready SLI Support Video Card 02G-P4-2662-KR off newegg, 114.99 total, before i did i checked for driver support, present for windows 7 through 10, linux ;) and mac someone in another forum post showed drivers for 10.8.2 i believe, so this card will work everywhere for me on all of my installs, yes i like to play with hackintosh it's entertaining :D

so if you want this hd 4650, send me a pm and we can work something out.

i was thinking something like $50 usd + shipping?

the driver just updated from the ppa i am using and the issue seems to be gone now, go figure the minute i order a new card lol, so you're in luck.

---

### Post by pooldemon6000 on 2015-09-26
> **mastablasta said:**
> you can however upgrade the opensource drivers. there are one or two descent PPA's for that. see if that solves the issue. if not then I am interested in the old card if you are from EU :P

maybe the forum didn't notify you, i am getting a different card within the week, if you want this one let me know.

---

### Post by pooldemon6000 on 2015-10-07
> **mastablasta said:**
> xorg edgers is another testing one: [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

also check if you can find any parameters you can use below the table: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/) 

as you can see not all features of r700 chip are enabled. AMD helped a bit but I am not sure if they will continue to help the opensource driver or if there is actually any movement for these a bit older models. in any case dont' expect "windows drivers performance". 

I have ATI 9600 - in windows it easily ran Morrowind and such in Linux it is overheating, struggling with any QIII engine game (overheating mostly). this is one of the reasons why I keep the PC with radeon 3650 loaded with WinXP. performance in Linux got better but is still not the same as on XP.

do you want the card?

if you do i'd be happy to send it.

---

### Post by Bashing-om on 2015-10-07
pooldemon6000; hello;

Do not think hard of me but:
```

sysop@1404mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon

```
I bought this card new some 6 years ago for $15.00 US .

[INDENT][INDENT]just food for thought
[/INDENT][/INDENT]

---

### Post by pooldemon6000 on 2015-10-11
yours is much older, also i said i'd be happy to send it, i looked it up and it is being sold on ebay for around $40.

i was offering to send it as in give it away.

i wouldn't think bad of you for trying to help inform, if mastablasta doesn't want it, anyone else?

the latest update i used from the ppa i mentioned has it working near flawlessly with mohaa under wine, didn't test much.

---

### Post by mastablasta on 2015-10-12
i would need to see if motherboard is compatible and i think it might not be a good idea to send it to me even for free. too much shipping costs.

i had a problme installing new nVidia card in that motherboard. i tried my 3650 and that card worked but was very slow. thinking back maybe i should have upgraded the kernel, but then again same card Works well on another slower PC. so thinking a bit more about it i believe that even 4650 would have the same issue. i am not sure why this happens. BIOS got an uprgade to support these cards, but maybe they work well on this motherboard only in Windows.


the nVidia, i tried to run could only show screen using nouveau (in crappy resolution) but as soon as I installed recomended drivers screen got blank on reboot (blinking cursor). so now I am stuck with the old AMD Radeon  9600 XT (that often overheats) which is why i was thinking that this one might work. but MIGHT. it could be I would pay quite a bit and got the same result. 

40 USD is probably a fair price. i don't know. i know these radeons for some reason still have their price. even here. i mean my GPU is porbably worth more than the whole PC combined. i can see why as i can still run many games desprite the old desktop that runs them.

the NVidia i tried was of similar power, but more ram. it cost 70 EUR here. but it didnt' work at all and i (and NVidia tech support) couldn't find out why not. so I returned the card to seller.

---

### Post by pooldemon6000 on 2015-10-12
> **mastablasta said:**
> i would need to see if motherboard is compatible and i think it might not be a good idea to send it to me even for free. too much shipping costs.

i had a problme installing new nVidia card in that motherboard. i tried my 3650 and that card worked but was very slow. thinking back maybe i should have upgraded the kernel, but then again same card Works well on another slower PC. so thinking a bit more about it i believe that even 4650 would have the same issue. i am not sure why this happens. BIOS got an uprgade to support these cards, but maybe they work well on this motherboard only in Windows.


the nVidia, i tried to run could only show screen using nouveau (in crappy resolution) but as soon as I installed recomended drivers screen got blank on reboot (blinking cursor). so now I am stuck with the old AMD Radeon  9600 XT (that often overheats) which is why i was thinking that this one might work. but MIGHT. it could be I would pay quite a bit and got the same result. 

40 USD is probably a fair price. i don't know. i know these radeons for some reason still have their price. even here. i mean my GPU is porbably worth more than the whole PC combined. i can see why as i can still run many games desprite the old desktop that runs them.

the NVidia i tried was of similar power, but more ram. it cost 70 EUR here. but it didnt' work at all and i (and NVidia tech support) couldn't find out why not. so I returned the card to seller.

I don't know how much it would be to ship it, I'm going to try and get a power supply that supports my new card today, pm me an address somewhere near you or yours and I'll see how much it is to ship, doubt it will cost that much.

---

