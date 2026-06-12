---
title: "How many dual video cards can I add to a single computer?"
date: 2008-07-09
forum: Hardware
---

### Post by PsychedelicWonders on 2008-07-09
?

What do I need to take into consideration if I want to run 4 monitors?

---

### Post by Daelyn on 2008-07-10
> **PsychedelicWonders said:**
> ?

What do I need to take into consideration if I want to run 4 monitors?

This doesn't have anything to do with linux, mate!

But, there is the option of having three nvidia X2 cards, or two ATI X2 cards.
It will be quite an expensive setup, though.

If you wanna even try to run it under linux, go for nvidia.

---

### Post by PsychedelicWonders on 2008-07-10
Uhh it kind of does since i'm going to be running linux, I want to make sure what I design is going to work on this OS platform.

So I just cant get 2 dual video cards like this one...?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049)

What makes the situation different that you would need something extra special?

---

### Post by phidia on 2008-07-10
> **PsychedelicWonders said:**
> Uhh it kind of does since i'm going to be running linux, I want to make sure what I design is going to work on this OS platform.

So I just cant get 2 dual video cards like this one...?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049)

What makes the situation different that you would need something extra special?

Do you want to use SLI? There are threads on setting up SLi in ubuntu see [this]("http://ubuntuforums.org/showthread.php?t=816843&highlight=sli"). The card you linked is a pci-x card. I don't know how many logicboards have more than two of those-anyway that will be your limit-the amount of pci-x slots on the board.

---

### Post by PsychedelicWonders on 2008-07-10
What is SLi exactly?

What is a logicboard?

---

### Post by tamoneya on 2008-07-10
the most dual video cards I have seen in one computer is four leading to 8 GPU cores.  Anything more than that and you would need some sort of custom motherboard because they physically wont fit in the slots.

[http://fastra.ua.ac.be/en/index.html](http://fastra.ua.ac.be/en/index.html)

---

### Post by tamoneya on 2008-07-10
> **phidia said:**
> Do you want to use SLI? There are threads on setting up SLi in ubuntu see [this]("http://ubuntuforums.org/showthread.php?t=816843&highlight=sli"). The card you linked is a pci-x card. I don't know how many logicboards have more than two of those-anyway that will be your limit-the amount of pci-x slots on the board.

I believe you mean pci express.  They are not the same thing.
[http://en.wikipedia.org/wiki/PCIX](http://en.wikipedia.org/wiki/PCIX)
[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

As for SLI i dont think you are going to want it.  It allows you to link multiple video cards to have them process for one monitor.  This is the opposite of what you are trying to do.  

The first thing you should consider is what you have for expansion slots.  If you dont have two PCI express slots you are going to probably end up using PCI graphics cards.  Take a look inside your computer.  If you dont know how to identify expansion slots please just post a picture and we can help you ID them.

---

### Post by phidia on 2008-07-10
> **tamoneya said:**
> I believe you mean pci express.  They are not the same thing.
[http://en.wikipedia.org/wiki/PCIX](http://en.wikipedia.org/wiki/PCIX)
[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

As for SLI i dont think you are going to want it.  It allows you to link multiple video cards to have them process for one monitor.  This is the opposite of what you are trying to do.  

Thanks for the correction I did mean pci express. I've built and helped to built several computers-I've never seen a logic/motherboard with more than 2 pci-express slots, but i guess they might be out there. 
The other thing to emphasis here is that running that many gpus will probably require an upgraded power supply.

---

### Post by soxs on 2008-07-10
> **phidia said:**
> Thanks for the correction I did mean pci express. I've built and helped to built several computers-I've never seen a logic/motherboard with more than 2 pci-express slots, but i guess they might be out there. 
The other thing to emphasis here is that running that many gpus will probably require an upgraded power supply.

I own such a rare one with 4 pci-e but *** soon I exceed 2 gpus, 2 lanes will be slowed down to x8 from x16, well.. a man madde bottleneck.

---

### Post by PsychedelicWonders on 2008-07-10
Alright here are the specs on the expansion slots on the mobo...

Expansion Slots 
PCI Express x16 - 2 x PCIe x16 (blue @ x16 mode, black @ x4 or x1 mode)  
PCI Express x1 - 2  
PCI Slots - 2  

So what does that all mean?

What is the difference between PCI Express x16 & PCI Express x1?

---

### Post by Cap'n Skyler on 2008-07-10
> **PsychedelicWonders said:**
> ?

What do I need to take into consideration if I want to run 4 monitors?

what linux do you have in mind?
i have dabbled in sabayon and it had awesome 3d that worked easy and no fuss.it seems to me it also supports 2 monitors as well.:popcorn:
no idea if/how teh 'buntu does there.

---

### Post by soxs on 2008-07-11
> **PsychedelicWonders said:**
> Alright here are the specs on the expansion slots on the mobo...

Expansion Slots 
PCI Express x16 - 2 x PCIe x16 (blue @ x16 mode, black @ x4 or x1 mode)  
PCI Express x1 - 2  
PCI Slots - 2  

So what does that all mean?

What is the difference between PCI Express x16 & PCI Express x1?
Speed x16 is 16 times faster than x1 (while x1 is still faster tha pci)

---

### Post by Opensource-student on 2008-07-11
PCI Express x16 = 16x Faster than just PCI
PCI Express X1  = just a PCI slot that you can put PCI Express cards in, may be x2 as fast as PCI (I am not sure) this wont however take advantge of PCI Express' x16 fast speed
PCI Slot = Basic expasion port
I think you could have 3 screens w/ 3 cards but I know almost nothing about Graphics card and connecting extra screens.
I belive you can add as many cards as you can fit (FPS EXTREME!!) but it would require software to split the desktop between more screens e.g. N tune for nvidia cards. I would like to know if there is an open source alterative but it may be because the different cards need different methods.
Don't quote me on this Check it out on the net but I hope it helps

Could this be moved to a a differnt section??

---

### Post by tamoneya on 2008-07-11
Okay this is good.  I would get 2 PCI express cards and you would get two additional monitors each.  If you tell us how much you are looking to spend on each card I can try and recommend some for you.  Also I am going to second that recommendation for a larger power supply.  Can you find out how much power your current one has.  It is in Watts so you are looking for something like 350 W or 500 W.

---

### Post by PsychedelicWonders on 2008-07-11
Just an FYI - this is for a new build, so I havent ordered any parts yet.

Alright here is the card I'm getting right now.  It is a dual DVI card...

1) so if I can in fact put 2 of these dual video cards on this machine?... I will hook up 3 regular lcd screens and eventually a 40" lcd tv for a total of 4.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500049)

For budget reasons, right now I am only going to get 1 and will get a second one in the future as an upgrade. 

2) Since I do in fact have 2 PCI X16, I might as well put my video cards in the best slots right?.

As far as addtional cards I plan on putting a sound card which is rated just PCI 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829102002](http://www.newegg.com/Product/Product.aspx?Item=N82E16829102002)

3) Is regular PCI enough for sound?

I also plan on putting in a tv tuner and possibly a raid card if needed.

4) Will both of these two be ok on PCI X1?

5) This way I can keep my video cards in the x16 slots?

The power supply I am going with right now is a 500W - 

6) is 500W enough for up to 4 monitors?

You guys keep reference graphics cards and video cards... 

7) But they are in fact the same thing right?

For the OS I will be using Ubuntu as my main and windows XP for other programs that wont run properly in Ubuntu.

I will run both OS on a single HDD by themselves that is partitioned.

---

### Post by tamoneya on 2008-07-11
I would bump it up to a bit more like 550 W.  It depends a little on your processor selection so 500 may be okay if you have a lower watt processor but I would make it 550 to be safe.

---

### Post by PsychedelicWonders on 2008-07-11
> **tamoneya said:**
> I would bump it up to a bit more like 550 W.  It depends a little on your processor selection so 500 may be okay if you have a lower watt processor but I would make it 550 to be safe.

here is the processor I am going to get... and I will probably overclock it to 3.0 as I hear this one is easy to do so.

Am I still ok with the 500W or do i need the 550w?

Is that really that big of a jump up on the wattage?

how do you figure out how large of a power supply is needed?

---

### Post by tamoneya on 2008-07-11
i dont see the link but judging by the fact that you say you are going to over clock to 3.0 i am guessing it is the Q6600 2.4 GHz quad core.  In that case I would go with the 550 W.  Will make the system more stable.  I bet it would run at 500 W but Im not positive and if it did it would be less stable and could result in increased component wear.

---

### Post by PsychedelicWonders on 2008-07-11
> **tamoneya said:**
> i dont see the link but judging by the fact that you say you are going to over clock to 3.0 i am guessing it is the Q6600 2.4 GHz quad core.  In that case I would go with the 550 W.  Will make the system more stable.  I bet it would run at 500 W but Im not positive and if it did it would be less stable and could result in increased component wear.

sorry...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017)

yeah you seem to know what youre talking about.  :)

So especially if I am going to overclock it AND run 4 monitors eventually, the 550W will be best for me?

how do you figure out how large of a power supply is needed?

When taking into account that i will be running two dual video cards with 4 monitors and overclocking...  how exactly did you come to the conclusion that I needed an extra 50W?

---

### Post by PsychedelicWonders on 2008-07-11
bump

---

### Post by alfalfa31 on 2008-07-11
I'm currently running 4 GPU's (I prefer to call them video cards), 4 monitors, but I have made all 8 monitors work at once (just to say I had done it).  I'd do it all the time, except for a little problem with desk realestate.

I have a really strange xorg.config file that I sort of stitched together and made pretty. Also (contrary to popular belief), ATI's do just fine with this setup.

I'm running 4 ATI Radeon HD 3650's, all 3d accelerated and (since I'm currently only running 4 monitors) the last two cards are set up in a nice little CrossFire chain with the first two.

I'd enclose a full screen, but not too many places will let you upload a 5920 x 1050 image (The left side (side 2) is 2560 x 1024 (1280 x 2) on two 17 inch LCD's, while the right side (side one) is 3360 x 1050 (1680 x 2) on twin 22 inch wide screen LCD's).  I'll e-mail it to you if you'd like.

So, in review, ATI works, you can run 8 monitors from 4 GPU's.  

As an aside, if you have a PCI slot or two, you can stick in an old Rage, SIS, MGA or some other such PCI thing for a potential two to 4 extra heads (I haven't tried, but I know I could make it work).  It wouldn't leave room for too much else, but if you like heads, why not...  

I used to have an old dual head PCI MGA, and I believe I had a dual head PCI Nvidia at one point (it came from a MAC).  Sky's the limit, my man (so long as the sky is 12 heads).

------------------------------------------
Mainboard: MSI K9A2 Platinum
Processor: AMD Phenom 9500
RAM:       8 Gig G-Skill PC 8500, Ganged
Video:     4 x ATI Radeon HD3650
OS:        Ubuntu 8.4.1 hardy (2.6.19)

---

### Post by alfalfa31 on 2008-07-11
A couple other issues you may need to entertain on the power supply and misc hardware stuff...

The overall wattage isn't as important as how that wattage is distributed over the respective rails (channels for power output).  

There are two basic schools of thought on this.  The first, and most common, is to divide the 12 volt output over several rails and rate the PSU based on a combined score of the rails (the number of rails ranges from two to 4).  The flaw in this approach is in assuming that novice users understand power draw and the requirements their hardware will place on the PSU.

The second method, and probably best for you, as you are asking quite a few newbie type questions (which is not to say that being a newbie is a bad thing, it just means that more people will try to help you), is to supply all the wattage down one rail, and let the board decide what to draw.  The obvious drawback is that if the single 12 V rail fails, the PSU is useless, but that's going to be the case with most PSU's even if only one rail fails.

So, a recommendation, based on the above...

Bigger numbers are better most of the time, but allotment is important as well.  That being the case, take a gander at this PSU...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139005](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139005)

It's affordable, powerful, efficient and no guesswork as to which rail to plug in where...

---

### Post by PsychedelicWonders on 2008-07-11
Do I really need to go up to 650W?

Or will 550W suffice?

---

### Post by tamoneya on 2008-07-11
i would go with this one.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817182030](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182030)

two rails and designed for a two graphics card system.  Plenty of 12 V amps and nice price.

---

### Post by kdorf on 2008-07-11
If you are going with two high end video cards you will probably actually want between 800-1000W power supply. Those things eat up a _LOT_ of power when they are maxed out.

---

### Post by tamoneya on 2008-07-11
> **kdorf said:**
> If you are going with two high end video cards you will probably actually want between 800-1000W power supply. Those things eat up a _LOT_ of power when they are maxed out.

I think you are talking more around a 8800 GTX.  These are not crazy high end.  They are 8600 series which run at about 80 W each.  That is only 160 W total more than a computer with integrate graphics.

I am running a very similar system to the OP with one 8600 GTS.  It has a 450 W power supply.  He is adding one 80 W card making 550 W sufficient.

---

### Post by Lord Xeb on 2008-07-11
What do you mean by dual graphics cards. If you mean the dual-core graphics cards, then  go for the nVidia Geforce 9 series or GTX 200 series. For the dualcore ATI series, it would be the HD 3000 X2 or the HD 4000 series.

---

### Post by tamoneya on 2008-07-11
by dual graphics cards he means two 8600 GTS cards in non sli mode.  He wants 4 monitors and since each card has 2 DVI ports you need two cards.

---

### Post by markbuntu on 2008-07-11
Power supplies will last longer and run cooler and more efficiently the further you are from maxing them out. 1000 watts would not be an inconsiderate choice for the system you are contemplating. Running a p/s at close to maximum for anything but extremely short periods is a recipe for disaster.

If you are going to run two of the newer high end graphics cards, they need 250 watts each and a quad core processor needs another 150-200. Then there is another 100-200 for everything else. That puts you at 800-900 watts already.

A rule of thumb for maximizing reliability in power supplies is 80% usage at maximum intermittent expected load. If the maximum load is continuos then it should be 60% -75%. If you are expecting to use a p/s in an unairconditioned space where ambient temperatures may exceed 40 degrees C, these percentages need to be downgraded a further 10-20%.

Just because some p/s is rated at 500w does not mean it can sustain that in any environment or for any length of time. I have seen undersized power supplies that failed due to the solder melting off the boards because they were running at 90-95% capacity for long periods of time or at 70% load in a harsh environment, like in an un-airconditioned house in Arizona in the summer.

---

### Post by soxs on 2008-07-12
> **Lord Xeb said:**
> What do you mean by dual graphics cards. If you mean the dual-core graphics cards, then  go for the nVidia Geforce 9 series or GTX 200 series. For the dualcore ATI series, it would be the HD 3000 X2 or the HD 4000 series.

X2 versions from ati/amd are NOT supported by the fglrx driver and too new to be suported with the opensource ones.

---

### Post by tamoneya on 2008-07-12
> **markbuntu said:**
> Power supplies will last longer and run cooler and more efficiently the further you are from maxing them out. 1000 watts would not be an inconsiderate choice for the system you are contemplating. Running a p/s at close to maximum for anything but extremely short periods is a recipe for disaster.

If you are going to run two of the newer high end graphics cards, they need 250 watts each and a quad core processor needs another 150-200. Then there is another 100-200 for everything else. That puts you at 800-900 watts already.

A rule of thumb for maximizing reliability in power supplies is 80% usage at maximum intermittent expected load. If the maximum load is continuos then it should be 60% -75%. If you are expecting to use a p/s in an unairconditioned space where ambient temperatures may exceed 40 degrees C, these percentages need to be downgraded a further 10-20%.

Just because some p/s is rated at 500w does not mean it can sustain that in any environment or for any length of time. I have seen undersized power supplies that failed due to the solder melting off the boards because they were running at 90-95% capacity for long periods of time or at 70% load in a harsh environment, like in an un-airconditioned house in Arizona in the summer.

The Q6600 G0 stepping has a TDP of 95 W making 150 W to 200 W overkill.
[http://processorfinder.intel.com/details.aspx?sSpec=SLACR](http://processorfinder.intel.com/details.aspx?sSpec=SLACR)

As for 250 W per video card that is also excessive.  If you look at the card the OP was looking at getting you will notice that it is not crazy high end (8600 GT) and it has just a PCI 6 pin connector.  This connector has specifications on it for 75 W.  [http://en.wikipedia.org/wiki/Graphics_card#Power_demand](http://en.wikipedia.org/wiki/Graphics_card#Power_demand)

While I do agree with your 80% rule I think that 550W will be sufficient even when you take into account sound cards and the other peripherals.

---

### Post by alfalfa31 on 2008-07-13
> **soxs said:**
> X2 versions from ati/amd are NOT supported by the fglrx driver and too new to be suported with the opensource ones.

I beg to differ, my man...  I posted earlier in this very thread the fact that I'm running 4 ATI HD 3650's, using the 8.6 fglrx.  They work, not only well, but throw over 6000 FPS for the default size glxgears, and over 500 FPS when I stretch the gears window to 3360 px wide.

---

### Post by soxs on 2008-07-13
> **alfalfa31 said:**
> I beg to differ, my man...  I posted earlier in this very thread the fact that I'm running 4 ATI HD 3650's, using the 8.6 fglrx.  They work, not only well, but throw over 6000 FPS for the default size glxgears, and over 500 FPS when I stretch the gears window to 3360 px wide.

w00t??? do you use crossfire, which would confuse me even more, as I read on phoronix.com that it will be implemented to the linux driver in the end of 2008??? Or did you put 4 videocards into your PC to connect 4 monitors??

---

### Post by alfalfa31 on 2008-07-13
> **soxs said:**
> w00t??? do you use crossfire, which would confuse me even more, as I read on phoronix.com that it will be implemented to the linux driver in the end of 2008??? Or did you put 4 videocards into your PC to connect 4 monitors??

Indeed...

I originally tried it with 8 monitors, and while it worked, it was just too big.  I now have four connected to the first two cards, and the second two are XFired to the first two respectively.

I'm telling you, what's possible, if you're willing to dig and work is far more than what the experts say.

Check the top of page three of this thread for details...

---

### Post by alfalfa31 on 2008-07-13
For defecation and giggles, here's the bottom of my "/etc/ati/amdpcsdb" file

```


[AMDPCSROOT/SYSTEM/Crossfire/chain]
NumChains=V2
[AMDPCSROOT/SYSTEM/Crossfire/chain/0]
Enable=V1
Master=V256
NumSlaves=V1
Slaves=R00050000
[AMDPCSROOT/SYSTEM/Crossfire/chain/1]
Enable=V1
Master=V512
NumSlaves=V1
Slaves=R00060000


```

^ 
|
|
|

See...  Told you it works... 

As you can see, the second two cards (PCI:5:0:0 and PCI6:0:0) are slaved...

---

### Post by alfalfa31 on 2008-07-13
Soxs,

I can't send you a personal message yet (despite the fact that I've been using Linux since 1995, I'm considered a noob here), so here are the requested links.

visit [http://www.theakkadian.com/images/Screenshot_full.jpg](http://www.theakkadian.com/images/Screenshot_full.jpg)

The desktop is pretty generic, as I have yet to tweak it, but it's a fresh shot...

I've taken the liberty of adding a shot of my actual desk so that you don't think I just GIMPed a pic together...

It's at visit [http://www.theakkadian.com/images/Screenshot_desk.jpg](http://www.theakkadian.com/images/Screenshot_desk.jpg)

All told, it's pretty sweet.

I built it on an MSI K9A2 Platinum with 8 Gig of PC8500 (1066), and of course the HD3650s.

You'll notice that I have VirtualBox running on the monitor second from the left, and the screenshot is of me writing this message.  The right center screen is a terminal showing the HD 3650's (toward the bottom)...

In the physical photo, ignore the mess.  You can see my Logitech MX Revolution in the foreground, my Krzr, a few tools, etc...  The monitor on the left is made out of parts of other monitors (I have piles of them).  You can faintly make out the words on the dumb terminal (old VT220) under the desk, and I use that for troubleshooting.  If I start X from the terminal, It's like a running error log.

Let me know what you think.  After all, if it weren't possible, would I be doing it?

Aaron

---

### Post by m.rankovic on 2008-07-13
alfalfa31, can u plaese post your xorg.conf? I have Radeon HD 2600 & Radeon x1600 and I can't get them to work together... I wont 2600 for my desktop and 1600 for TV... Help.. pls :) tnx... :)

---

### Post by alfalfa31 on 2008-07-13
Here she be...

Notice, though that the devices are listed for the two cards I'm using as slaves, but they are not screened.  I only put them in there to suppress the (WW) concerning not having a device section for them in the log.  They're otherwise useless.  Also, if you're doing TV out, you may want to omit the "Composite" "disable" line.



```


Section "ServerLayout"
	Identifier   "Default Layout"
	Screen    0  "screen1" 0 0
	Screen       "screen2" LeftOf "screen1"
	InputDevice  "Generic Keyboard"
	InputDevice  "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	     "dbe"
	SubSection   "extmod"
		Option 	    "omit xfree86-dga"
	EndSubSection
	Load 	     "glx"
	Load         "dri"
	Load	     "freetype"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "envision"
EndSection

Section "Monitor"
	Identifier   "kiog"
EndSection

Section "Device"
	Identifier  "ati1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "UseFastTLS" "0"
	Option	    "HWCursor" "on"
	Option	    "BackingStore" "false"
	Option 	    "XAANoOffscreenPixmaps" "true"
	Option	    "OpenGLOverlay" "off"       
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
	Option	    "TextureVideo" "true"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "horizontal"
	BusID       "1:0:0"
EndSection

Section "Device"
	Identifier  "ati2"
	Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "BackingStore" "false"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "OpenGLOverlay" "off"        
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "TextureVideo" "true"
        Option      "OverlayOnCRTC2" "1"
        Option      "DesktopSetup" "horizontal"
	BusID       "2:0:0"
EndSection

Section "Device"
        Identifier  "ati3"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "BackingStore" "false"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "OpenGLOverlay" "off"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "TextureVideo" "true"
        Option      "OverlayOnCRTC2" "1"
        Option      "DesktopSetup" "horizontal"
        BusID       "5:0:0"
EndSection

Section "Device"
        Identifier  "ati4"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "BackingStore" "false"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "OpenGLOverlay" "off"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "TextureVideo" "true"
        Option      "OverlayOnCRTC2" "1"
        Option      "DesktopSetup" "horizontal"
        BusID       "6:0:0"
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "ati1"
	Monitor    "envision"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen2"
	Device     "ati2"
	Monitor    "kiog"
	DefaultDepth     24
EndSection

Section "ServerFlags"
	Option    "AllowMouseOpenFail" "on"
	Option    "IgnoreABI" "on"
	Option    "AIGLX" "on"
EndSection

Section "Extensions"
	Option    "Composite" "disable"
	Option	  "Damage" "true"
EndSection

Section "DRI"
	Group     0
	Mode      0666
EndSection


```

Questions, comments?

---

### Post by markbuntu on 2008-07-13
So, I guess you are not running compiz on that are you?

I have VideoOverlay "off" and BackingStore "true" but otherwise it is the same setup as you. With compiz I turn TexturedVideo "off" so the videos don't flicker in windowed mode. I really wish they would fix that.

I am running my single HD3650 1GB with big desktop running 24 and 19 inch monitors. I have absolutely no room for anymore, I don't even think I could squeeze in another 24 to replace the 19.

---

### Post by alfalfa31 on 2008-07-13
No compiz, but as soon as I figure out a couple more issues, I'll turn it back on.

Sorry to hear about that monitor issue.  If it's desk space, check freecycle or Craig's list.  If it's house space, move ;)

---

### Post by m.rankovic on 2008-07-13
> **alfalfa31 said:**
> Questions, comments?

:( My comp crash

Here is my xorg.conf
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Screen0" 0 0
	Screen		"Screen1" LeftOf "Screen0"
EndSection

Section "InputDevice"
	Identifier	"Logitech UltraX"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc105"
	Option		"XkbLayout" "rs,rs"
	Option		"XkbVariant" "latin,"
	Option		"XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Razer DeathAdder"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Resolution" "1800"
	Option		"SampleRate" "1000"
EndSection

Section "Monitor"
	Identifier	"Samsung 226BW"
EndSection

Section "Monitor"
	Identifier	"Samsung PS-42C62H"
EndSection

Section "Device"
	Identifier	"Radeon HD 2600XT"
	Driver		"fglrx"
	Option          "XAANoOffscreenPixmaps" "on"
	Option          "TexturedVideo" "on"
	Option          "UseFastTLS" "0"
	Option          "BackingStore" "0"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Radeon X1600"
	Driver		"fglrx"
	Option          "XAANoOffscreenPixmaps" "on"
	Option          "TexturedVideo" "on"
	Option          "UseFastTLS" "0"
	Option          "BackingStore" "0"
	BusID		"PCI:2:0:0"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Radeon HD 2600XT"
	Monitor		"Samsung 226BW"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Radeon X1600"
	Monitor		"Samsung PS-42C62H"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "ServerFlags"
	Option		"AIGLX" "on"
EndSection

Section "Extensions"
	Option		"DAMAGE" "on"
	Option		"Composite" "off"
EndSection

```

This is from xorg log file:
```

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) AIGLX: Suspending AIGLX clients for VT switch

```

And when I use only one monitor, I get this error in xorg:
```
(EE) fglrx(0): PreInitCFChain failed
```

P.S. My eng. is #%"#& ... sorry :)

---

### Post by alfalfa31 on 2008-07-13
Interesting...

You have a crossfire chain set up, and it isn't working.

run 

```
sudo aticonfig --lsch
``` 

and see what it tells you.

If it tells you anything other than "no chains found," delete the chains with 

```
sudo aticonfig --cfd --adapter=all
```

If it returns that you have no chains configured then check /etc/ati/amdpcsdb for references to crossfire chains, and comment them out (make a backup before you change any of this stuff).

Look for things like this

```

[AMDPCSROOT/SYSTEM/Crossfire/chain]
NumChains=V1
[AMDPCSROOT/SYSTEM/Crossfire/chain/0]
Enable=V1
Master=V256
NumSlaves=V1
Slaves=R00050000

```

Where it says "Slaves=R000500000" yours will have the number of the PCI slot in which the system finds the card (i.e. if your slave is in the second PCI slot (PCI:2:0:0) then it will read "Slaves=R000200000"). 

I would lose the mode lines.  The monitors will tell the cards what they can handle and the card will only send them their max resolution.

Can you give me a grep of all the EE's and WW's in the xorg log?

```
cat /var/log/Xorg.0.log | grep EE && cat /var/log/Xorg.0.log | grep WW 
``` 

Also, don't apologize for your English.  I'm pretty sure it's better than me trying to speak your language...

---

### Post by m.rankovic on 2008-07-13
sudo aticonfig --lsch returns "No CrossFire chains defined" and I dot have "[AMDPCSROOT/SYSTEM/Crossfire/chain]" lines in amdpcsdb

```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): PreInitCFChain failed
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): Unable to register ADL handler for 0x00110000
(WW) fglrx(0): Unable to register ADL handler for 0x00120000
(WW) fglrx(0): Unable to register ADL handler for 0x00130000
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) Razer DeathAdder: No Device specified, looking for one...

```

---

### Post by PsychedelicWonders on 2008-07-14
xorg.conf


What exactly is that?

Looking at those screen shots you guys posted of all that data... makes me scared to try ubuntu because I have no idea what any of that is.

Is there like a Ubuntu for dummies book or section of this website on how to work in ubuntu from the intial 1st bootup?

---

### Post by alfalfa31 on 2008-07-14
> **PsychedelicWonders said:**
> xorg.conf


What exactly is that?

Looking at those screen shots you guys posted of all that data... makes me scared to try ubuntu because I have no idea what any of that is.

Is there like a Ubuntu for dummies book or section of this website on how to work in ubuntu from the intial 1st bootup?

We are your Ubuntu for dummies book.  Think about it.  Where else can you ask the book the question you want answered and have it tell you what chapter to read without looking through the table of contents.

What you want to do is not exactly simple, even in winders.  There are things you would have to tweak to make it work right.

All the stuff you're reading is just the way of tweaking in Linux.  It doesn't make sense now, but it will once you play with it a bit.  It's like when you learned to speak.  It didn't happen overnight.  You weren't born like Stewie from Family Guy, right...

M.Rankovich, of this thread speaks Serbian.  That would require a "for dummies" book on my part, because I don't speak Serbian.  He's taking English instructions, though.  Kind of takes the "excuse factor" out of it, right?

Hell, I'll bet it took you a bit of time to learn to make winders do what you wanted it to do, didn't it?  You didn't start out even knowing how to cut/copy/paste, did you?

I say that the trade off of a tiny bit steeper learning curve is more than worth the price of admission.  You have full control instead of "In communist Russia, computer uses YOU!"

That's my two cents...

---

### Post by alfalfa31 on 2008-07-14
> **m.rankovic said:**
> sudo aticonfig --lsch returns "No CrossFire chains defined" and I dot have "[AMDPCSROOT/SYSTEM/Crossfire/chain]" lines in amdpcsdb

```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): PreInitCFChain failed
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): Unable to register ADL handler for 0x00110000
(WW) fglrx(0): Unable to register ADL handler for 0x00120000
(WW) fglrx(0): Unable to register ADL handler for 0x00130000
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) Razer DeathAdder: No Device specified, looking for one...

```

OK...

As it turns out, even if you didn't use crossfire, you'd get that error.  I've been using it, so I haven't seen it.  I shut it off and get the same thing, despite the fact that there are no chains defined.

So, that brings us back to the problem of the crash.  In your "ServerLayout" section, you have no input devices defined.  I'm more inclined to believe that to be your problem than drivers.

Give it a shot and see what happens.

```

Section "ServerLayout"
        Identifier   "Default Layout"
        Screen    0  "screen1" 0 0
        Screen       "screen2" LeftOf "screen1"
        **InputDevice  "Generic Keyboard"**
        **InputDevice  "Configured Mouse"**
        Option       "AIGLX" "on"
EndSection

```

By the way, you need to change the "configured mouse" thing to the name of your mouse, and add this somewhere to your config file for the keyboard (assuming you're using the US layout).

```

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

```

---

### Post by m.rankovic on 2008-07-15
still crashing :(

---

### Post by alfalfa31 on 2008-07-15
> **m.rankovic said:**
> still crashing :(

Can you send your current xorg.conf file and the whole Xorg.0.log?  I think if we go through it one line at a time, the answer will jump out...

---

### Post by m.rankovic on 2008-07-15
xorg.conf
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Screen0" 0 0
	Screen		"Screen1" LeftOf "Screen0"
	InputDevice	"Logitech UltraX" "CoreKeyboard"
	InputDevice	"Razer DeathAdder" "CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Logitech UltraX"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc105"
	Option		"XkbLayout" "rs,rs"
	Option		"XkbVariant" "latin,"
	Option		"XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Razer DeathAdder"
	Driver		"mouse"
	Option		"Device" "/dev/input/mice"
	Option		"CorePointer"
	Option		"Resolution" "1800"
	Option		"SampleRate" "1000"
EndSection

Section "Monitor"
	Identifier	"Samsung 226BW"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Samsung PS-42C62H"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Radeon HD 2600XT"
	Driver		"fglrx"
	Option          "XAANoOffscreenPixmaps" "on"
	Option          "TexturedVideo" "on"
	Option          "UseFastTLS" "0"
	Option          "BackingStore" "0"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Radeon X1600"
	Driver		"fglrx"
	Option          "XAANoOffscreenPixmaps" "on"
	Option          "TexturedVideo" "on"
	Option          "UseFastTLS" "2"
	Option          "BackingStore" "0"
	BusID		"PCI:2:0:0"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Radeon HD 2600XT"
	Monitor		"Samsung 226BW"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Radeon X1600"
	Monitor		"Samsung PS-42C62H"
	DefaultDepth	24
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "ServerFlags"
	Option		"AIGLX" "on"
EndSection

Section "Extensions"
	Option		"DAMAGE" "on"
	Option		"Composite" "on"
EndSection

```

Xorg.0.log
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux ubuntu 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 15 18:45:35 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Samsung 226BW"
(**) |   |-->Device "Radeon HD 2600XT"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Samsung PS-42C62H"
(**) |   |-->Device "Radeon X1600"
(**) |-->Input Device "Logitech UltraX"
(**) |-->Input Device "Razer DeathAdder"
(**) Option "AIGLX" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "DAMAGE" is enabled
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,277c card 8086,5842 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,277d card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 8086,0417 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,27e2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 8086,5842 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 8086,5842 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 8086,5842 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 8086,5842 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 8086,5842 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b0 card 8086,5842 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 8086,5842 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c1 card 8086,5842 rev 01 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 8086,5842 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,9588 card 1043,01c4 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,aa08 card 1043,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: 02:00:0: chip 1002,71c2 card 1462,0400 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,71e2 card 1462,0401 rev 00 class 03,80,00 hdr 00
(II) PCI: 04:00:0: chip 8086,109a card 8086,30a5 rev 00 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x00003fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xa0200000 - 0xa02fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xa0100000 - 0xa01fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xa0400000 - 0xa04fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:5), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xa0000000 - 0xa00fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x9588) rev 0, Mem @ 0x80000000/28, 0xa0200000/16, I/O @ 0x3000/8, BIOS @ 0xfffe0000/17
(--) PCI: (2:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0x90000000/28, 0xa0100000/16, I/O @ 0x2000/8, BIOS @ 0xfffe0000/17
(--) PCI: (2:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xa0110000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[1] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[2] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[3] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[4] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[5] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[6] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[7] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[8] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[12] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[13] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[14] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[15] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[16] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[22] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[23] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[24] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[1] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[2] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[3] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[1] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[2] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[3] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[4] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[5] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[6] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[7] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[8] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[12] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[13] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[14] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[15] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[16] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[22] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[23] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[24] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[1] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[2] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[3] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[5] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[6] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[7] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[8] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[9] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[10] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[11] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[14] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[15] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[20] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[21] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[22] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[23] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[24] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[25] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[31] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[32] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[33] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.50.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.50.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.501                    
(II) ATI Proprietary Linux Driver Build Date: Jun  2 2008 22:47:36
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9588) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[5] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[6] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[7] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[8] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[9] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[10] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[11] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[14] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[15] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[20] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[21] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[22] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[23] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[24] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[25] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[31] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[32] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[33] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f81e0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[5] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[6] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[7] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[8] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[9] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[10] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[11] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[14] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[15] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[20] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[21] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[22] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[23] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[24] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[25] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[31] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[32] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[33] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(1): pEnt->device->identifier=0x7f86b0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[5] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[6] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[7] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[8] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[9] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[10] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[11] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[12] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[14] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[15] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[25] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[26] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[27] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[28] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[29] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[30] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[31] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[37] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[38] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[39] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[40] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[41] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[44] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "TexturedVideo" "on"
(**) fglrx(0): Option "DPMS"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 2600 XT" (Chipset = 0x9588)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x01c4)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0x80000000
(--) fglrx(0): MMIO registers at 0xa0200000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.57
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV630
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.50.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 27f  Serial#: 1296380466
(II) fglrx(0): Year: 2007  Week: 38
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) fglrx(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HSDP924092
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d7f023232454d
(II) fglrx(0): 	26110103802f1e782ad515a455499a27
(II) fglrx(0): 	145054bfef80b30081808140714f0101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	3600da281100001a000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	00485344503932343039320a2020002f
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000010
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 36 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (90, 88)
(--) fglrx(0): Virtual size is 3360x1050 (pitch 3392)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Virtual size is 3360x1050 (pitch 3392)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Virtual size is 3360x1050 (pitch 3392)
(--) fglrx(0): *Mode 3360x1050 (unnamed)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=2
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(1): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) fglrx(1): PCI bus 2 card 0 func 0
(II) fglrx(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(**) fglrx(1): Option "UseFastTLS" "2"
(**) fglrx(1): Option "TexturedVideo" "on"
(**) fglrx(1): Option "DPMS"
(II) fglrx(1): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(1): RGB weight 888
(II) fglrx(1): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(1): Gamma Correction for I is 0x06419064
(==) fglrx(1): Gamma Correction for II is 0x06419064
(==) fglrx(1): Buffer Tiling is ON
(WW) fglrx(0): Unable to register ADL handler for 0x00400000
(--) fglrx(1): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(1): (PciSubVendor = 0x1462, PciSubDevice = 0x0400)
(--) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(1): Linear framebuffer (phys) at 0x90000000
(--) fglrx(1): MMIO registers at 0xa0100000
(==) fglrx(1): ROM-BIOS at 0x000c0000
(II) fglrx(1): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(1): Using adapter: 2:0.0.
(II) fglrx(1): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(1): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(1): PCIE card detected
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(1): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(1):  Display1: No EDID information from DDC.
(II) fglrx(1):  Display1: Failed to get EDID information. 
(II) fglrx(1): Primary Controller - CRT on secondary DAC
(II) fglrx(1): Internal Desktop Setting: 0x00000010
(II) fglrx(1): POWERplay version 3.  1 power state available:
(II) fglrx(1):   1. 500/396MHz @ 0Hz [enable load balancing]
(WW) fglrx(1): Unable to register ADL handler for 0x00110000
(WW) fglrx(1): Unable to register ADL handler for 0x00120000
(WW) fglrx(1): Unable to register ADL handler for 0x00130000
(==) fglrx(1): Qbs is not supported in this release. Disabled.
(==) fglrx(1): FAST_SWAP disabled
(==) fglrx(1):  PseudoColor visuals disabled
(==) fglrx(1): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(1): Center Mode is disabled 
(==) fglrx(1): TMDS coherent mode is enabled 
(II) fglrx(1): Total of 27 modes found for primary display.
(--) fglrx(1): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(1): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(1): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(1): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(1): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(1):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(1):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(1): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(1):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(1): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync (37.0 kHz)
(**) fglrx(1): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(1):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(1):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(1): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(1): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(1): *Mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(1): Modeline "720x576"x50.0   26.56  720 736 808 896  576 577 580 593 +hsync (29.6 kHz)
(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(1): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(==) fglrx(1): DPI set to (96, 96)
(--) fglrx(1): Virtual size is 3200x1200 (pitch 3200)
(**) fglrx(1): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(1): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(1): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(1): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(1):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(1):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(1): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(1):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(1): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync (37.0 kHz)
(**) fglrx(1): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(1):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(1):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(1): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(1): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(1): *Mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(1): Modeline "720x576"x50.0   26.56  720 736 808 896  576 577 580 593 +hsync (29.6 kHz)
(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(1): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(1): Virtual size is 3200x1200 (pitch 3200)
(**) fglrx(1): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(1): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(1): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(1): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(1):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(1):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(1): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(1):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(1): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync (37.0 kHz)
(**) fglrx(1): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(1):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(1):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(1): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(1): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(1): *Mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(1): Modeline "720x576"x50.0   26.56  720 736 808 896  576 577 580 593 +hsync (29.6 kHz)
(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(1): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(1): Virtual size is 3200x1200 (pitch 3200)
(--) fglrx(1): *Mode 3200x1200 (unnamed)
(**) fglrx(1): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(1): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(1): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(1): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(1):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(1):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(1): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(1):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(1): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync (37.0 kHz)
(**) fglrx(1): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(1):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync (43.0 kHz)
(**) fglrx(1):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(1): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(1): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(1): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(1):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(1): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(1): *Mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(1): Modeline "720x576"x50.0   26.56  720 736 808 896  576 577 580 593 +hsync (29.6 kHz)
(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(1): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(1): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(==) fglrx(1): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(1): Capabilities: 0x00000000
(==) fglrx(1): CapabilitiesEx: 0x00000000
(==) fglrx(1): cpuFlags: 0x8000001d
(==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(1): ATI GART size: 255 MB
(II) fglrx(1): [pcie] 261120 kB allocated
(II) fglrx(1): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(1): UseFastTLS=2
(==) fglrx(1): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B]
	[1] 1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B]
	[2] 0	0	0xa0200000 - 0xa020ffff (0x10000) MX[B]
	[3] 0	0	0x80000000 - 0x8fffffff (0x10000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xa0000000 - 0xa001ffff (0x20000) MX[B]
	[9] -1	0	0xa0210000 - 0xa0213fff (0x4000) MX[B]
	[10] -1	0	0xa0304000 - 0xa03043ff (0x400) MX[B]
	[11] -1	0	0xa0304400 - 0xa03047ff (0x400) MX[B]
	[12] -1	0	0xa0300000 - 0xa0303fff (0x4000) MX[B]
	[13] -1	0	0xa0110000 - 0xa011ffff (0x10000) MX[B](B)
	[14] -1	0	0xa0220000 - 0xa023ffff (0x20000) MX[B](B)
	[15] -1	0	0xa0200000 - 0xa020ffff (0x10000) MX[B](B)
	[16] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[17] -1	0	0xa0120000 - 0xa013ffff (0x20000) MX[B](B)
	[18] -1	0	0xa0100000 - 0xa010ffff (0x10000) MX[B](B)
	[19] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[24] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[25] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[26] 1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[27] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[30] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[31] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[32] -1	0	0x000040a0 - 0x000040af (0x10) IX[B]
	[33] -1	0	0x000040e0 - 0x000040e3 (0x4) IX[B]
	[34] -1	0	0x000040c0 - 0x000040c7 (0x8) IX[B]
	[35] -1	0	0x000040e4 - 0x000040e7 (0x4) IX[B]
	[36] -1	0	0x000040c8 - 0x000040cf (0x8) IX[B]
	[37] -1	0	0x000040b0 - 0x000040bf (0x10) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x00004020 - 0x0000403f (0x20) IX[B]
	[43] -1	0	0x00004040 - 0x0000405f (0x20) IX[B]
	[44] -1	0	0x00004060 - 0x0000407f (0x20) IX[B]
	[45] -1	0	0x00004080 - 0x0000409f (0x20) IX[B]
	[46] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[47] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[50] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[51] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x4c09000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.50.3
(II) fglrx(0):     Date: Jun  2 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x04c0b000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01090000
(II) fglrx(0): FBMM initialized for area (0,0)-(3392,1280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(3392,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 3392 x 230
(**) fglrx(0): Option "BackingStore" "0"
(**) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 26
(**) fglrx(0): Option "XaaNoOffscreenPixmaps" "on"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Finished Initialize PPLIB!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) fglrx(1): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(1): detected X.org 7.1.0.90
(II) fglrx(1): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(1): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(1): [drm] framebuffer handle = 0x4c14000
(II) fglrx(1): [drm] added 1 reserved context for kernel
(II) fglrx(1): X context handle = 0x1
(II) fglrx(1): DRIScreenInit done
(II) fglrx(1): Kernel Module Version Information:
(II) fglrx(1):     Name: fglrx
(II) fglrx(1):     Version: 8.50.3
(II) fglrx(1):     Date: Jun  2 2008
(II) fglrx(1):     Desc: ATI FireGL DRM kernel module
(II) fglrx(1): Kernel Module version matches driver.
(II) fglrx(1): Kernel Module Build Time Information:
(II) fglrx(1):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(1):     Build-Kernel __SMP__:            yes
(II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(1): [drm] register handle = 0x04c16000
(II) fglrx(1): Interrupt handler installed at IRQ 16.
(II) fglrx(1): Exposed events to the /proc interface
(II) fglrx(1): DRI initialization successfull!
(II) fglrx(1): FBADPhys: 0xc0000000 FBMappedSize: 0x010b3000
(II) fglrx(1): FBMM initialized for area (0,0)-(3200,1368)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(3200,1200) (front color buffer - assumption)
(II) fglrx(1): Largest offscreen area available: 3200 x 168
(**) fglrx(1): Option "BackingStore" "0"
(**) fglrx(1): Backing store disabled
(**) fglrx(1): DPMS enabled
(**) fglrx(1): Textured Video is enabled.
(II) fglrx(1): GLESX enableFlags = 16
(II) fglrx(1): GLESX is enabled
(**) fglrx(1): Option "XaaNoOffscreenPixmaps" "on"
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		25 128x128 slots
(II) fglrx(1): Acceleration enabled
(II) fglrx(1): [DRI] installation complete
(II) fglrx(1): Direct rendering enabled
(==) fglrx(1): Silken mouse enabled
(==) fglrx(1): Using hardware cursor
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:2:0:0

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7fc87da9d100]
2: /usr/lib/dri/fglrx_dri.so [0x7fc8753ab40f]
3: /usr/lib/dri/fglrx_dri.so [0x7fc87536fc98]
4: /usr/lib/dri/fglrx_dri.so [0x7fc8753d3e53]
5: /usr/lib/dri/fglrx_dri.so [0x7fc8753bd86f]
6: /usr/lib/dri/fglrx_dri.so [0x7fc8753d5098]
7: /usr/lib/dri/fglrx_dri.so [0x7fc874e76078]
8: /usr/lib/dri/fglrx_dri.so [0x7fc874eae9e5]
9: /usr/lib/dri/fglrx_dri.so [0x7fc874eb043e]
10: /usr/lib/dri/fglrx_dri.so [0x7fc8749f0e61]
11: /usr/lib/dri/fglrx_dri.so [0x7fc87505847f]
12: /usr/lib/dri/fglrx_dri.so [0x7fc87506cd08]
13: /usr/lib/dri/fglrx_dri.so [0x7fc87506cf8e]
14: /usr/lib/dri/fglrx_dri.so(__driCreateNewScreen_20050727+0x425) [0x7fc87551dfb5]
15: /usr/lib/xorg/modules/extensions//libglx.so [0x7fc87ca9fada]
16: /usr/lib/xorg/modules/extensions//libglx.so(__glXInitScreens+0x8d) [0x7fc87ca7168d]
17: /usr/bin/X(InitExtensions+0x7e) [0x4ad27e]
18: /usr/bin/X(main+0x2c7) [0x4369e7]
19: /lib/libc.so.6(__libc_start_main+0xf4) [0x7fc87da891c4]
20: /usr/bin/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) AIGLX: Suspending AIGLX clients for VT switch

```

---

### Post by m.rankovic on 2008-07-22
bump

---

### Post by soxs on 2008-07-22
lol, as far as I see you don't load a single module, add this and you should be fine (restart X/reboot of course):
```
Section "Module"
	Load		"bitmap"
	Load		"vbe"
	Load		"ddc"
	Load		"freetype"
	Load		"int10"
	#		Load		"type1"
	Load		"glx"
	Load		"dri"
	Load		"extmod"
EndSection
```

---

