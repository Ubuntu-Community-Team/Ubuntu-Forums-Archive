---
title: "Upgrading advise...compatibilty"
date: 2011-01-05
forum: Hardware
---

### Post by Fixitall on 2011-01-05
Hi all,
 
I want to upgrade my system and want to know what brands to choose to get good support by ubuntu. Some say linux is not well supported by some manufacturers.
 
The list of my preferred hardware components:
 
[FONT=Calibri]CPU[/FONT]
[FONT=Calibri]AMD Phenom II X6 1055T or[/FONT]
[FONT=Calibri]CPU[/FONT]
[FONT=Calibri]AMD Phenom II X4 955 Black Edition[/FONT]
[FONT=Calibri]MB[/FONT]
[FONT=Calibri]Asus M4A88TD-M EVO/USB3 | 90-MIBD05-G0EAY00Z or[/FONT]
[FONT=Calibri]MB[/FONT]
[FONT=Calibri]Asus M4A88TD-M/USB3 | 90-MIBD95-G0EAY0WZ[/FONT]
[FONT=Calibri]MEM[/FONT]
[FONT=Calibri]OCZ Gold DDR3 PC3-10666[/FONT]
[FONT=Calibri]8GB Dual Channel DDR3-kit or[/FONT]
[FONT=Calibri]MEM[/FONT]
[FONT=Calibri]Kingston ValueRAM KVR1333D3N9K2/4G[/FONT]
[FONT=Calibri]4GB Dual Channel DDR3-kit[/FONT]
[FONT=Calibri]HDD[/FONT]
[FONT=Calibri]Crucial RealSSD C300 2.5" 64GB[/FONT]
[FONT=Calibri]64GB SSD with SATA-600-connection[/FONT]
[FONT=Calibri]VIDEO[/FONT]
[FONT=Calibri]Sapphire HD 6870 1GB GDDR5 PCIE[/FONT]
[FONT=Calibri]Radeon HD6870 op 900MHz met 1GB GDDR5 or[/FONT]
[FONT=Calibri]VIDEO[/FONT]
[FONT=Calibri]Sapphire HD 6850 1GB GDDR5 PCIE[/FONT]
[FONT=Calibri]Radeon HD6850 op 775MHz met 1GB GDDR5[/FONT]
 
 
Any advise is appreciated.
 
Thanks.

---

### Post by snowpine on 2011-01-05
Hi Fixitall, you may find this list helpful:

[http://webapps.ubuntu.com/certification/](http://webapps.ubuntu.com/certification/)

---

### Post by Fixitall on 2011-01-06
Hi snowpine,
 
Thanks for the link. It is however not what I am looking for. It only addresses off the shelve systems / notebooks.
 
My system is customized with all kinds of components from different suppliers.
 
I am curious if AMD processors and MB chipsets are supported without problems. That's why I chose for an ASUS motherboard. And what about Radeon video cards?

---

### Post by snowpine on 2011-01-06
> **Fixitall said:**
> Hi snowpine,
 
Thanks for the link. It is however not what I am looking for. It only addresses off the shelve systems / notebooks.
 
My system is customized with all kinds of components from different suppliers.
 
I am curious if AMD processors and MB chipsets are supported without problems. That's why I chose for an ASUS motherboard. And what about Radeon video cards?

Sorry I was not more clear with my suggestion. You should take a look at the supported off the shelf systems to see if they have similar hardware to what you are proposing. If the components you are considering are also used in Ubunt-supported systems, then there is a good chance they will also work well with your custom build.

You can also use the forum Search feature to see if any users have reported problems/solutions for the hardware you are considering.

ASUS is a well-respected motherboard manufacturer, so I predict you'll have no problem. :)

---

### Post by cascade9 on 2011-01-06
AMD chipsets have good support with linux distros. The only tricky bits can be the onboard network and sound chips. To be honest, 'm not sure about the M4A88TD-M boards. I *think* they should work, but I havent checked. 

Unless you want a microATX system or need the onboard video for some reason, a 870 or 890FX chipset motherboard is a better idea. 

AMD 6XXX cards still have no offical linux support. They work with linux, btu you have to manually install the driers, then do a hack if you want to get rid of an 'unsupported hardware' watermark. 

nVidia has better proprietary drivers anyway, and if you are looking at cards like the 6850 and 6870 you are probably a gamer so you would want the proprietary drivers (better 3D performance than the open sopurce drivers) If you arent a gamer, dont even think about those expensive cards. ;) 

RAM isnt really an OS support issue. If the motherboard works with the RAM, it should be no problem. 

The SSD should be good as well.   [FONT=Calibri]

[/FONT]

---

### Post by Fixitall on 2011-01-07
Hi Cascade9,
 
Thanks for the info. I already came across a post of yours pointing at the AMD 870 Mainboards roundup of xbitlabs: [http://www.xbitlabs.com/articles/mainboards/display/amd-870-roundup.html](http://www.xbitlabs.com/articles/mainboards/display/amd-870-roundup.html)
Very helpfull.
 
The reason I am looking for a microATX MoBo is that I want to fit it in an existing case (silverstone GD05). I did quite some work to integrate a nice computer station in my livingroom furniture and am happy with it. The cabinet is not very deep so the GD05 fits perfectly. It needs some work though to make it all fit.
 
All micro ATX boards come with onboard graphics it seems. Thanks to your post I am also considering a Gigabyte MoBo but the choice is limited (microATX formfactor)
 
Options I found with the AMD 880G/SB850 chipset:
 
Asus M4A88TD-M EVO/USB3 | 90-MIBD05-G0EAY00Z
Asus M4A88TD-M/USB3 | 90-MIBD95-G0EAY0WZ
Gigabyte GA-880GMA-UD2H (rev. 2.1)
 
The issues you mention with ethernet and onboard sound, is that related to the MoBo? In other words, has a Gigabyte MoBo less issues?
 
Support of the AMD 6xxx videocards, why are they not officially supported yet in linux. They are already around for a year or so or not? Is this something AMD has to do (release a linux driver) or is this on the side of the linux distro's. I am not sure how this works.
The installation procedure and hack, do you have a link to a description of this so I have an idea what I get myself into.
 
Somebody told me that the linux support of Nvidia cards used to be bad and the AMD's very good. But nowadays this situation is reversed. Is that true?
 
What equivalent Nvidea card would you recommend? To my knowledge, the 6850 and 6870 are the mainstream gamer cards that have a decent price/ performance ratio.
 
Thanks for your advise.

---

### Post by cascade9 on 2011-01-07
OK, with a microAT case you will needa microATX moterhboard, that makes sense. Looking at the silverstone page though, you could have trouble fitting a 'gaming' card in there- 

[http://www.silverstonetek.com/products/p_spec.php?pno=GD05&area=usa](http://www.silverstonetek.com/products/p_spec.php?pno=GD05&area=usa)

A 86870, 6850 (or nvidia equivilent) should fit, just, but its going to be tight. Heat output could be a problem as well. 

I've never heard that ATI used to have better support. Maybe it was true a long time ago? 

Neither nvidia or ATI (OK, AMD now) have prefect linux support. Generally, AMD has better open source drivers, nVidia better closed source drivers. The closed drivers are always made by the video chip maker. The open soruce drivers could be make either by the community (nouveau for nvidia) or they can have some chip maker support (IIRC ATI has added code to some of the open soruce ATI drivers) 

I really dont know why AMD hasnt got drivers out for the 6XXX series cards. BTW, they were only released in late october 2010. 

The nearest equivilent to the 6850/6870 would be a GTX460. Similar prices, similar performance.   

> **Fixitall said:**
> All micro ATX boards come with onboard graphics it seems. Thanks to your post I am also considering a Gigabyte MoBo but the choice is limited (microATX formfactor)
 
Options I found with the AMD 880G/SB850 chipset:
 
Asus M4A88TD-M EVO/USB3 | 90-MIBD05-G0EAY00Z
Asus M4A88TD-M/USB3 | 90-MIBD95-G0EAY0WZ
Gigabyte GA-880GMA-UD2H (rev. 2.1)
 
The issues you mention with ethernet and onboard sound, is that related to the MoBo? In other words, has a Gigabyte MoBo less issues?

Its a pity that nobody has made a 770/790X/790FX/870/890FX motherbaord in microATX. (AFAIK anyway, somebody might have got one out that I've failed to notice)  

880G/SB850 is the most current choice. Yuo can still get old 780/785 etc chipset motherbaords, but 880/SB850 is worth it just for SATAIII. 

Yes, the ethernet/sound issues are relased to the motherboard. The motherboard makers can put lots of different networking and sound chips on the motherbaord, and not all of them are that happy with linux (eg, VIA 1708S sound chips, there has been more than a few problems with them). 

I know that the Gigabyte GA-880GMA-UD2H (and USB version, same motherboard with a USB3.0 chip) has Realtek 8111D network, I've got the same nework chip in my motherbaord and it works well with all teh linux distros I've used.  Thjere is also a Realtek ALC892 sound chip that should be fine.

---

