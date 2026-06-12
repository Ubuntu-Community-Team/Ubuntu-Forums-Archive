---
title: "Need advice on motherboard and GPu compatibility"
date: 2010-03-29
forum: Hardware
---

### Post by mastablasta on 2010-03-29
I am interested in this motherboard (due to AGP socket):
[http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2](http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2)
 
Among main concerns is this note:
**Audio**- 7.1 CH Windows® Vista™ Premium Level HD Audio (ALC888 Audio Codec)
 
I googled and it seems someone with an older version of Ubuntu managed to get it work, yet plenty people with other distros had problems (inlcuding SATA recognision and Audio). If it owrks with Ubuntu i plan to stick a celeron in it. 
 
I also have an old Radeon 9600 XT, which i would like to stick inside. Will it work with Ubuntu?
 
At the moment Ubuntu system uses old AMD 733 Mhz, 16 MB ATI Rage and 1.3 GB DDR ram. I plan to stick a 2+ Ghz Celeron to new system and reuse the DDR and old AGP card.

---

### Post by cascade9 on 2010-03-29
The realtek ALC888 should work. Even if it doesnt work out of the box, there are linux drivers up on the realtek site (my 889 didnt work out of the box with some older distros, but I havent had to install the drivers on newer distros) 

9600XT should work. IIRC, ATI has discontinuted driver support for the 9600XT, but it will run with older drivers. 

BTW- AMD 733? Never existed as far as I know. 700 and 750 are around (athlon and duron) but no 733. Also, DDR? Its possible, but most 700750s would have come with SD RAM. 

1.3GB is strange as well.... 1GB + 256MB sticks are the closest I can think of.

---

### Post by mastablasta on 2010-03-29
> **cascade9 said:**
> The realtek ALC888 should work. Even if it doesnt work out of the box, there are linux drivers up on the realtek site (my 889 didnt work out of the box with some older distros, but I havent had to install the drivers on newer distros) 
 
9600XT should work. IIRC, ATI has discontinuted driver support for the 9600XT, but it will run with older drivers. 
 
BTW- AMD 733? Never existed as far as I know. 700 and 750 are around (athlon and duron) but no 733. Also, DDR? Its possible, but most 700750s would have come with SD RAM. 
 
1.3GB is strange as well.... 1GB + 256MB sticks are the closest I can think of.
 
Thanks, that is some good news (i guess). I will then probably go ahead with upgrade...well actually depends on the money if i have any left and if i can get the darn TV tuner to work in Ubuntu.
 
well it says AMD II 733Mhz (after BIOS starts up) or something like that. yes, that is correct it's a DDR 256MB+1GB, onbly it is showing in some OS as 1.3 GB :D

---

### Post by cascade9 on 2010-04-07
Finally, I lost this thread (too busy with other stuff). 

I've had a look around,and I still cant find a 733 AMD. It might be that you have had your BIOS settings go odd (it happens) and something has underclocked your CPU. Its more than likely you have a 1100Mhz Duron or Athlon thats not running @ the proper 100Mhz, its been slowed down to 66Mhz. 

You could try going into your BIOS and checking....733 to 1100 is a nice jump ;)

Could you please post your output for lspci and lscpu? I'm really wondering how this 733 thing happened.

*Edit-i just tired the xorg-video-ati (free) driver and it seemed to work really well. Of course, ubuntu might take a while to get the version I just tried but its a good sign for future use.

---

### Post by mastablasta on 2010-04-08
lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

```
lscpu
```
Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            6
Model:                 8
Stepping:              0
CPU MHz:               733.388
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K
```

BAM! 733Mhz

It actually says Athlon 733CMhz That C is strange isn't it?

---

### Post by mastablasta on 2010-04-08
Ok so i went to windows partition and used everest home edition there and guess what?!

I found this:
    Motherboard: 
      CPU Type                                          AMD Athlon XP, 733 MHz (5.5 x 133) 
      Motherboard Name                                  Matsonic MS8137C(+)  (5 PCI, 1 AGP, 1 CNR, 4 DIMM, Audio) 
      Motherboard Chipset                               VIA VT8366A Apollo KT266A 
      System Memory                                     1280 MB  (DDR SDRAM) 
      BIOS Type                                         Award Modular (01/10/03) 
      Communication Port                                Communications Port (COM1) 
      Communication Port                                Communications Port (COM2) 
      Communication Port                                ECP Printer Port (LPT1)

But i also found this:
  [ Processors / AMD Athlon(tm) XP ] 
 
    Processor Properties: 
      Manufacturer                                      AMD 
      Version                                           AMD Athlon(tm) XP 
      External Clock                                    133 MHz 
      Maximum Clock                                     1500 MHz 
      Current Clock                                     733 MHz 
      Type                                              Central Processor 
      Voltage                                           1.5 V 
      Status                                            Enabled 
      Upgrade                                           ZIF 
      Socket Designation                                Socket A

Could it be 1500 Mhz Athlon in here? and if so how come it always ran on 733 Mhz? Even more there doesn't seem to be any settin for CPU speed in BIOS. There is a clock setting that has some Mhz and is currently set at default. It has a few other settings only i am a bit afraid to mess with them. Unless i can find a manual for the Mobo:).

Funny though in Windows My Computer-> Properties also says  Athlon Xp (tm) 733Mhz.

---

### Post by cchhrriiss121212 on 2010-04-08
Yes, thats an 1.5Ghz athlon you've got there. You can safely increase the clock speed up to 1500Mhz in bios (most cpus can be safely overclocked with adequate cooling). The OS is correctly recognising the speed the cpu has been set to as it has been underclocked at some point.

---

### Post by mastablasta on 2010-04-09
Problem is there is no setting in bios that would say 733 Mhz or have an option 1500Mhz. Maybe it's like 5.5x133Mhz only higher?! I will try and search for this one and increase it. I just hope i dont' fry anything. 
 
Processor has standard cooler with a fan on top (no watter cooling or any fancy stuff like that).
 
 
Is it possible that different RAM modules would mess up the frequency? one was old 256 MB and one is newer 1 GB (both DDR)

---

### Post by cchhrriiss121212 on 2010-04-09
Your RAM has nothing to do with it. Go into bios and you can increase the clock speed incrementally, just stop when it reaches 1500 and there is no risk of you frying your hardware.

---

### Post by cascade9 on 2010-04-09
I'm sure there is a linux command that would tell me more, but I cant recall what it is now. :( 

5.5 x 133? o.O Something weird there. Same with 1.5Ghz max clock speed, unless its rounding....there are 1466Mhz Athlons (XP 1700+, 133 x 11) and 1533Mhz (XP 1800+ 133 x 11.5) but no 1.5Ghz Athlons.

It cant be an overclocked Athlon 550 (100 x 5.5) because that had 512K cache, and ran at 1.6volt, and was a different motherboard, 'slot a' (your board is 'socket a').

It could be that everest is reporting the FSB Mhz and multipiler wrong. If it is wrong, instead of 133 x 5.5 you would need 266 x 5.5 for 1466Mhz. Or it could be that you have an unlocked CPU, and instead of running the proper 11 x 133, its running 5.5 x 133. Hard to tell.

I'll have to go and have a look at everest...er..maybe, anyway, if I can find my install discs for XP. Been a while since I've seen it so I'm not sure how it does things. 

I would guess that its a XP 1700+ that has been underclocked- stock they ran at 1.6v or 1.75v, depending on if they were palmino or thoroughbred. By 'always ran this way', did you buy it new, or 2nd hand? Was it sold as a 733Mhz AMD?

---

### Post by mastablasta on 2010-04-10
hmm i found thisreply online to a similar quesiton:
> All Athlons were until a few months ago named on a power rating, not  actual CPU speed rating. Since you didn't tell me the exact type of your  processor i believe that it's the actual , normal speed of your CPU.  But if it isn't then it's underclocked. To verify that go in the BIOS  and see if the FSB is the correct value - 133MHz - sometimes it's at the  default value of 100MHz. This can be changed from 2 locations:
1 -  the JP4 jumper on the motherboard - 2-3 corresponds to 133MHz (of course  you should change it only with the pc is disconnected from the mains)
2  - in BIOS go to Frequency/Voltage Control - CPU Host Clock and set it  to 133. The thing is that  > Frequency/Voltage Control - CPU Host Clock is indeed set on default. I found the manual for the mobo, and it says that this funciton is used for overclocking the CPU.But is it safe to just increase it to a higher value?

I am also trying to find a newwer version of bios. maybe it would be a good idea to upgrade it first before attempting to increase the frequency.

EDIT: The mainboard model is Matsonic MS8137C+ with a VIA KT266A Chipset Socket A.

---

### Post by cascade9 on 2010-04-11
I hada  look at the Matsonic site, and it appeared to have no BIOS update for the MS8137C+. Its possibel that you could flash the BIOS from a different manufacturers version of the KT266A, but I wouldnt try it unless you had to. 

I think its more likely that your multiplier is wrong than the FSB (CPU Host Clock). From what I remember, an unlocked Palamino/T'bred CPU defaults to a multi of 5.5 (which would explain the 133 x 5.5). 

As for what the CPU is really rated at....maybe try the command 'lshw' but if that still gives you "AMD 733" then the only way to be sure is by checking the hardware, by pulling of the heatsink and checking the actual chip markings.  

BTW, changing the CPU Host Clock 			 		is sort of safe- with your current Mhz, the CPU should run much higher than 133Mhz FSB, but as to how well the chipset would deal with it is unknown. It would be overclcokcing the nchipset to go past 133Mhz, and as with all overclcocking, there are risks (so, for example, 134Mhz would probably be fine, 200 is right out)

I would try to change the multiplier. 

BTW, whoever you quoted above is wrong- 

> All Athlons were until a few months ago named on a power rating, not  actual CPU speed rating. 

Athlons started out as being rated by CPU speed rating (Mhz, 550-1400) then moved to a 'power' rating (XP1600+ onward). AMD never went back to a speed rating.

---

### Post by mastablasta on 2010-04-11
I just increased it ot max 150/38 or something like that.

now it says:
```
     *-cpu
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.0
          size: 850MHz
          width: 32 bits

```

and
```

Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            6
Model:                 8
Stepping:              0
CPU MHz:               825.135
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K
```

SO 850Mhz. Is that correct? Or is it overclocked?

If it's 850 or close and not over 1000Mhz i think it will sill be better to replace it with a newer Motherboard and some 2Ghz celeron or something. computer will be used for office tasks, listening music and if i can make TV tuner work also temporary TV.

---

### Post by cascade9 on 2010-04-11
> **mastablasta said:**
> I just increased it ot max 150/38 or something like that.

150/38 is FSB/PCI Mhz. normally it should be 133/33, but the PCI speed is determined by dividing the FSB by 4 (for 133 operation), so when you up the FSB to 150Mhz, it devides that by 4 = 38Mhz (actually 37.5)

> **mastablasta said:**
> 
now it says:
```
     *-cpu
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.0
          size: 850MHz
          width: 32 bits

```and
```

Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            6
Model:                 8
Stepping:              0
CPU MHz:               825.135
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K
```SO 850Mhz. Is that correct? Or is it overclocked?

Underclocked CPU, overclocked FSB. 

> **mastablasta said:**
> 
If it's 850 or close and not over 1000Mhz i think it will sill be better to replace it with a newer Motherboard and some 2Ghz celeron or something. computer will be used for office tasks, listening music and if i can make TV tuner work also temporary TV.

Its got to be at least 1000Mhz stock, the slowest Athlon with a 133 FSB was the Athlon 1000C ("C" for 133 FSB). 

With it being a 1.5volt chip, I can say its not a 1000C. Its got to be an Athlon XP, possibly a late model Athlon XP-M (mobile). There are various Athlon XP chips, with various voltages so its hard to be sure without checking the chip.

I really wouldnt 'upgrade' to a 2Ghz Celeron- if you can get the chip going at even XP 1700+ speeds (and that is the slowest chip I think it could be) then it would be faster than a 2Ghz celeron. 

Try to change the multiplier, not the FSB- like here- 

[IMG]http://img.tomshardware.com/us/2001/11/12/plastic_surgery/bios3.jpg[/IMG] 

[http://www.tomshardware.com/reviews/plastic-surgery,387-8.html](http://www.tomshardware.com/reviews/plastic-surgery,387-8.html)

Go for x 11 and try that..if it works, that is running at 1700+ speeds. Its more than possible that you could get more multiplier- up to x 13.5 (2200+), or even x15 (2400+) but I would guess that x11-x12.5 would be the original rated speed from AMD.

---

### Post by mastablasta on 2010-04-12
Ok. this will have to wait until next weekend when i get my hands on it again. :-) will post an update then.
computer doesn't have so many options to choose from in BIOS that's why i was hoping  anew version of BIOS could show some light. I think i can take a pic with a camera next time. It should be Athlon XP i believe. It's a desktop so it's probably not mobile version.
 
Ugh, if i can't figure it out i will just pull of the heatsink and read the chips description...

---

### Post by mastablasta on 2010-04-16
i am attaching the pictures of all available options. I can not find any other option in BIOS to change anything. Except maybe DRAM clock if it would have any effect.

Any option than the highest selected one gives me less than 850Mhz. So it would appear that's the max i can get on this motherboard?!

EDIT: Actuall the max is then 825Mhz ?! WTF?!

---

### Post by cascade9 on 2010-04-17
Changing the DRAM/PCI clock wont have any effect on your CPU speed. 

Hmm...

You've got to be able to get more than 850Mhz on that motherboard, the KT266a always did (it was released about the same time as the XP 1600+, 1.4Ghz, which was the 1st CPU to commonly be used with the KT266a). 

As for why you cant get more....well, this is a guess- its one of two things. Either you have a CPU released after your last BIOS update, and it defualts back to the minimum multipiler (5.5), or, far more liekly, its a mobile XP (and still defaults back to the minimum 5.5 multi)

What motherboard is it? All I can see from the end of the BIOS bootscreen is '7C+' and that is not quite enough to tell. 

Yes, 825Mhz. 5.5 x 150Mhz. Its just rounded up to a 'normal' CPU speed.

---

### Post by mastablasta on 2010-04-17
Motherboard is **Matsonic MS8137C+** and it looks like BIOS is already somehwat updated, since i have a manual for it and manual doesn't mention CPU voltage regulator. perhaps it would need more voltage. I checked the jumper settings and there are only two settings for CPU frequency and that is 100 Mhz and 133Mhz. 

Ugh i don't know anymore it all seems a bit strange here. The computer was assembled at some local company some time ago. Its quite possibel they udnerclocked it but i wonder why they would do such a thing. i mean surelly a customer buying 1500Mhz processor would object when they saw only 733. Like i said computer wasn't mine before. i will see if i can maybe find a bill for it to see what it says in the specifications :-)

Motherboard certainly is old...

---

### Post by gordintoronto on 2010-04-17
> **mastablasta said:**
> I am interested in this motherboard (due to AGP socket):
[http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2](http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2)...
 
I also have an old Radeon 9600 XT, which i would like to stick inside. Will it work with Ubuntu?
 
At the moment Ubuntu system uses old AMD 733 Mhz, 16 MB ATI Rage and 1.3 GB DDR ram. I plan to stick a 2+ Ghz Celeron to new system and reuse the DDR and old AGP card.

I don't believe in pouring money into old technology. For example, you could go to a system such as:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103235&cm_re=atom_ion-_-83-103-235-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103235&cm_re=atom_ion-_-83-103-235-_-Product) 

It would be much higher performance than what you are looking at, and within a year you would save the price difference by using less electricity.

There are similar systems available with no operating system installed, if you want to avoid the Microsoft Tax.

---

### Post by cascade9 on 2010-04-18
Sorry abotu askignthe motehrboard type. I completely forgot that you had already put it in. :| 

Anyway, after figuring out what the 'normal' ECS motehrboard version of that board is (a K7VTA3 V2.x) it appears to not have a multiplier adjustment. Bah. :( 

> **mastablasta said:**
> Ugh i don't know anymore it all seems a bit strange here. The computer was assembled at some local company some time ago. Its quite possibel they udnerclocked it but i wonder why they would do such a thing. i mean surelly a customer buying 1500Mhz processor would object when they saw only 733. Like i said computer wasn't mine before. i will see if i can maybe find a bill for it to see what it says in the specifications :-)

Motherboard certainly is old...

I think there is onyl 2ways this would happen- AMD made a mistake (eg, they didnt 'lock' the multiplier, or put the wrong CPU into the box) or the assembler made a mistake (used the wrong CPUin the system). 

I wouldnt be suprised if the customer never noticed, I know lots of people who dont pay any attention to the boot-up messages. Probably the majority of people dont. 

Pretty easy for the assembler to miss that sort of thing as well. When you have 5+ computer builds going on, in a business envirotment, you tent to not look at the details like the bootscreen- to busy doing other stuff. 

Its a pity, but you probably cant get that CPU going at proper speed on that mohterboard. :( 

I wish I could have a (physical) look at it, its probably a nice CPU.

---

