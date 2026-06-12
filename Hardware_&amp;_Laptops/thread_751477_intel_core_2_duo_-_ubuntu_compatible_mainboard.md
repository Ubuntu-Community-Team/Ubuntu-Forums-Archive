---
title: "intel core 2 duo - ubuntu compatible mainboard"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by chris_pmf on 2008-04-10
After reading some threads about abit ip35 and ubuntu I think it's better not to buy this board?!

Which board would your recommend when I need:
- at least 2 PCI Slots (for WinTV-PCI and a SB-Live EMU10k1)
- 1 IDE Port (HL-DT-ST DVDRAM GSA-4120B)

I want to buy the following:
- Core2 Duo E8400
- Leadtek Winfast (G92) 8800GTS (512MB)
- Corsair XMS2 DHX CL4 (DDR2 - PC 800)
- SATA2 500 GB Seagate ST3500320AS
- Xigmatek HDT-S1283 (CPU heat sink)
- **mobo?**

Is the above hardware ubuntu compatible and which mobo should I buy?

Thanks :)

---

### Post by Existentialist on 2008-04-10
You can see in my sig that I am running a similar system and everything works great in hardy 8.04, though I can't speak for the Win TV-PCI card.  I think the motherboard will depend on what you plan to do with the system.  If you don't plan on running extreme overclocks or 3-way sli in the future you don't need a 780i, but something like the new 750i would work.  I have always liked the nvidia chipsets, and judging by your choice of hardware I'm assuming you are looking for a more performance oriented motherboard.  So I guess my suggestion would be to look in to a 7-series chipset board (750i, 780i, 790i).

---

### Post by chris_pmf on 2008-04-10
Your assumption is almost perfect :)

Though I likely won't use SLI, because of the huge power consumption.

So I'am looking for a optimal: performance + price + power consumption ;)

Which specific board(s) would you recommend?

Thanks

---

### Post by Existentialist on 2008-04-11
Well brand wise, it's up to you.  I like EVGA due to there warranty and support, but others like BFG or XFX are good also.  As for the boards, for the 45nm processors you will probably want to go 680i or higher with the nvidia chipsets.  Generally prices are as follows:

680i~$160+
750i~$150+
780i~$250+
790i~$300+ (plus DDR3 ram, which is not cheap yet)

I think for your build I would stick with the 680i, or the 750i.  EVGA just put out a new version of their 750I with solid state capacitors that should OC nicely.  Here's a link from newegg:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188026](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188026)

Last thing, you didn't mention what power supply you are going to be using.  Make sure you don't go too cheap on the psu or you will encounter problems with these higher performance parts.

---

### Post by chris_pmf on 2008-04-11
Thanks, what would you say to the MSI P7N SLI Platinum?

I hoped that I can use my "old" Enermax 460W power supply?

---

### Post by Existentialist on 2008-04-11
Board looks good to me.  As for the psu, does it have the newer 8-pin cpu connector and separate 6-pin pcie connectors for the gpu?  If not I would recommend a newer one which will probably have stronger 12V rails to support the new gpu.

---

### Post by chris_pmf on 2008-04-11
It's the Enermax EG465AX-VE... is this one ok?

---

### Post by Existentialist on 2008-04-11
It looks like the 33A rail should be enough, it might be cutting it close though.  That is an ATX1.3 psu, while the new motherboards are ATX2.2 so I'm not sure if you will have the auxiliary power connector for the cpu.  I'm not 100% on this, but if it works you may be limiting the cpu's stability a little especially if you overclock.

Power supplies are not that expensive (as long as you stay under 1000watts), and often newer ones will be more efficient.  I would spend the extra to ensure you get all of your new components the power they need rather than risk stability issues and shortening the lifespan of your new parts.

---

### Post by chris_pmf on 2008-04-11
[COLOR=Silver]Ok and how much watts will I need for this system?

[COLOR=Black]I just ordered:

- 1x 512MB Gainward Geforce 8800GTS DDR3 2xDVI TVOut PCIe
- 1x Netzteil ATX Enermax MODU82+ 625 Watt ATX 2.3
- 2x 500GB Seagate ST3500320AS Barracuda 7200rpm SATA 32MB
- 1x Xigmatek HDT-S1283 Heatpipe Cooler 120mm
- 1x 4096MB Corsair DDR2 XMS2 800MHz 128Mx8 DRAMs
- 1x MSI P7N SLI Platinum 750i SLI S775 FSB 1333MHz PCe ATX
- 1x Intel Core 2 Duo E8400 3.00GHz 1333MHz S775 6MB 45nm Box

Thanks again for your help! :)
[/COLOR][/COLOR]

---

### Post by Existentialist on 2008-04-11
Good choice, I'm running a 520 watt corsair psu in the system in my sig, and I would still be comfortable running an additional 8800gts on it, so I think you should have more than enough power.

Let me know if you have any other questions when setting it up or installing.

---

### Post by chris_pmf on 2008-04-12
I updated my order, because I found a better and cheaper psu ;)
(updated the list above, too)

Do your Sound Blaster X-Fi Fatal1ty works with Ubuntu? Because I thought about buying a new SB-Card (maybe).

---

### Post by Existentialist on 2008-04-12
Creative does not offer any decent level of support for linux on their cards.  I use my onboard sound in linux, and will not by another creative product again.  Try out the onboard, it is pretty good, before deciding on buying anything else.

---

### Post by chris_pmf on 2008-04-20
Back again ... I installed everything and so far it works really great but I have one last problem...

**top** and **free -m** shows me only 3gb memory! why?

Thanks again :)

---

### Post by Existentialist on 2008-04-20
Did you install the 32-bit version?  You will get around 2.75-3.00GB with the 32-bit kernel.  The 64-bit will let you address all 4GB+.

---

### Post by chris_pmf on 2008-04-20
Yes, because I thought the ubuntu guys build the kernel with the option*CONFIG_HIGHMEM64G*.
Currently I compile the newest kernel 2.6.25 like [described here]("http://ubuntuforums.org/showthread.php?t=311158") with this option changed.

I hoped there is an easier way... you know one?

PS: I don't use the 64-bit version because of the problems other wrote about flash, ...

---

### Post by Existentialist on 2008-04-20
Unfortunately, if the kernel isn't compiled for the higher memory, recompiling is the only way for all of the RAM to be addressed.

Might be worth trying the 64-bit since it is easier than recompiling.  I've never used anything but the 64-bit version of ubuntu and never ran into any issues with flash before.  You could always try to get it working with the live cd version first to make sure you can do everything you want.

---

### Post by chris_pmf on 2008-04-20
Is it possible to "upgrade" from 32 to 64-bit without a complete reinstall?

---

### Post by SuperAndy on 2008-04-21
no, you will have to reinstall. you can seperate your home folder using [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") guide, to make that transition a bit easier.

i am actually quite glad i found this thread. i have recently upgraded my computer, core 2 quad and 4gb of RAM. i installed hardy x64 RC, and its fantastic. rock solid, and flash works flawlessly. It uses some nspluginwrapper i think i read, that installs the adobe flash linux plugin in 64bit firefox 3. really good.

and today, i bought an 8800 GTS to go with the system. from everything i have seen and read, it seems to work well in hardy, so i am happy!

one thing by the way, i dont know what motherboard you are using, but if it is asus you have to enable memory remapping in the BIOS to access all the RAM, even if you are running a x64 OS.

---

### Post by chris_pmf on 2008-04-21
> **SuperAndy said:**
> no, you will have to reinstall. you can seperate your home folder using [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") guide, to make that transition a bit easier.
Thanks, I already found the answer to my question... so right now I have already reinstalled :)
(have my /home on a separate partition since dapper, I think)

> **SuperAndy said:**
> one thing by the way, i dont know what motherboard you are using, but if it is asus you have to enable memory remapping in the BIOS to access all the RAM, even if you are running a x64 OS.
I bought this one:
> **chris_pmf said:**
> [COLOR=Silver][COLOR=Black]...
[/COLOR][/COLOR] - 1x MSI P7N SLI Platinum 750i SLI S775 FSB 1333MHz PCe ATX
...

So far everything seems to work ... installing FF is a little bit more work, but it's ok and well [documented]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins").

---

### Post by yekim on 2008-05-31
Hey guys, wow am I glad I found this thread - THANKS!

I am buying the MSI P7N SLI Platinum, an Intel e8400, 4GB Mushkin mem (thanks for the x64 version note), and a Gigabyte 8800GT.

A couple quick questions ...

Chris_pmf - Are you still happy with the MSI?  Are you using RAID?  I'm a bit concerned as my current NForce4 does not handle NVRaid gracefully in Ubuntu.

Also, has anyone tried running Team Fortress 2 under Wine with this type of setup?  My current setup runs it pretty poorly, tends to crash/hang/etc.  I am hoping it is just poor performance (AMD X2 4200+, 1GB RAM, and 6800GT).

Thanks, -yek

---

### Post by chris_pmf on 2008-05-31
> **yekim said:**
> Chris_pmf - Are you still happy with the MSI?
Yeah, totally...

the config is just awesome fast :)

I'm not using raid... I have my home on a different hdd (sdb) than my system partitions (sda), so I get the best possible performance and I don't have to worry about my /home when anything goes wrong.

I play non native games on WinXP (extra partition on sda), because I don't want to mess with wine.

---

