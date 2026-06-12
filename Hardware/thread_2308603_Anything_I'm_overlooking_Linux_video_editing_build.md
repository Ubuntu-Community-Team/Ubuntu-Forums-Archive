---
title: "Anything I'm overlooking? Linux video editing build."
date: 2016-01-04
forum: Hardware
---

### Post by Bucky Ball on 2016-01-04
Hi all,

Trying to edit high res video on a 32bit P4 with 4Gb of RAM (and only three of it being seen and used) isn't going to work. So, the time has come to build a new machine (my current desktop is about thirteen years old so don't really need an excuse).

Audio is my main thing but in the past, at the moment and at times in the future, I am going to need to edit high quality, not 4k for now, video (1920x1080p @ 50fps will be about it). See below the hardware components I have selected for the build. My question(s) is, not being a vid expert, will this do the job and will rendering still take longer than the clip I am rendering? Am I missing a bottleneck somewhere (is it called hardware parallelism?)? i.e. is data going to bottleneck anywhere when transcoding or doing anything else video related?

I know this rig will be fine, real fine, for my audio stuff, and have checked that the important bits - CPU, motherboard, vid card - will work with Ubuntu (I'm intending to do this project in Ubuntu) and they appear to.
 
All comments, thoughts, experiences, gratefully accepted.

[Gainware GTX 970 phantom vid card]("http://www.gainward.com/main/vgapro.php?id=953")
[ASrock H110-HDV motherboard]("http://asrock.com/mb/Intel/H110M-HDV/?cat=Specifications")
[Coolermaster 700w PSU]("http://www.coolermaster.com/powersupply/b-series/b700ver2/")
[Intel Core i7-6700k CPU]("http://www.msy.com.au/sa/adelaide/pc-components/15984-intel-bx80662i76700k-core-i7-6700k-40ghz-8mb-lga1151-skylake-boxed-cpu.html")
[Kingston 16Gb HyperX Fury RAM kit]("http://www.msy.com.au/sa/adelaide/pc-components/15916--kingston-hyperx-fury-hx421c14fbk2-16-16gb-kit-8gx2-ddr4-2133-desktop-ram.html")
[Coolermaster Silencio 452 case]("http://www.coolermaster.com/case/mid-tower-silent-series/silencio452/")

I have an SSD and hard drives and an old Hoontech PCI audio card which I'll be chucking in there. That has worked fine out of the box in Ubuntu for years, works fine now, so all good there. 

From the PSU calculators I've used, a 700W PSU seems a bit like overkill, but who knows what the future may bring ...

PS: I've looked around for ready built 'barebones' systems - lot more convenient for me as don't really have the time to build a computer right now - and have seen some that are close to these specs, but not quite there in some significant way. Shudder to think what the stores would want to slug me for this specific build. Stretching the purse strings as is. :-k :|

... but I'm planning on it lasting me another ten years!

---

### Post by sandyd on 2016-01-04
Note that kdenlive has no GPU acceleration for encoding, and will not use the video card unless special patches are applied. The patches are ages old by now, and probably don't work. As a result, encoding speed will be restricted by the CPU. There are some effects (movit) that will use the video card, but that is probably it.

---

### Post by Bucky Ball on 2016-01-04
Great heads up, sandyd. Thanks. Never would have known anything about that. Is there any vid app in Ubuntu that will utilise the card fully? I see the Nvidia site has Linux drivers for it.

And does it look capable apart from that, hardware-wise? :)

---

### Post by sandyd on 2016-01-04
> **Bucky Ball said:**
> Great heads up, sandyd. Thanks. Never would have known anything about that. Is there any vid app in Ubuntu that will utilise the card fully? I see the Nvidia site has Linux drivers for it.

And does it look capable apart from that, hardware-wise? :)

Hardware should be fine:

LightWorks comes to mind, the last time I heard, they use pixel shaders, which will use the GPU.

---

### Post by Bucky Ball on 2016-01-05
Lightworks looks good, also expensive, but not really for what it is I guess. I may be able to get an education discount as this project is for uni.

sudodus pointed me to [this site]("http://www.ggsdata.se/index-en.php") which has Core i7 laptops with pretty much the same hardware I'm looking at using (see the Core i7-6700s down the bottom of page). The seller's in Sweden, I'm in Australia, and the machines are extremely expensive anyway, but it does confirm that the hardware I'm intending to use is going to work fine for Ubuntu and will play nice with each other. 

The seller probably mentions the motherboards they use on the product details page but I don't read Swedish. :|

---

### Post by Bucky Ball on 2016-01-13
Well, still going with this. CPU, case, PSU, RAM, I'm happy with. Still stuck on the motherboard and graphics so hoping for further comment. 

Still keen on the Gainward GTX 970 Phantom as it appears to be the quietest there is for my budget (will also be using this machine for audio so as quiet as possible for the budget good). 

My two question marks are is it possible to squeeze a 2.5x graphics card on a microATX board (I could get away with one PCI slot for the sound card but have also selected a more expensive ATX motherboard as a Plan B), and secondly, will this Gainward device work okay with Linux?

I'm imagining the main detail is that it is 'NVidia GTX 970' and we know that works (taking into account sandyd's caveats), but wondering if there's any oddities with this brand/model and Linux. Anyone got any experience with Gainward graphics?

Also, if Kdenlive isn't going to use the card and Lightworks appears to be the only option, how do people edit HD footage on Linux, or don't they? Is it with integrated graphics or some other type of graphics card? Should I forget about doing this on Linux if I'm needing to use a higher-end video card and focus my efforts on Windows, as much as I'd rather not?

(As I mentioned, I don't know a lot about what's required for editing video nowadays. Building an audio rig, fine. About to drop a wad of cash on a graphics card for the first time ever and don't want to stuff it up so excuse me for feeling a bit sweaty and unsteady about the final decision. If I had a couple of months to do more research I'd feel a bit more confident about it. ;))

---

### Post by J_Me on 2016-01-13
Do you already have a CPU heatsink, if not something by Noctua maybe.

---

### Post by Bucky Ball on 2016-01-14
Okay, I figure if I'm going to do it, may as well go all the way (within reason). 

The final (I hope) hardware list is in the attached pic. Add to this [the Kingston RAM]("http://www.allneeds.com.au/prod1615.htm"). Anything missing or obviously going to not play nice?

@J_Me: Don't know if you mean a heatsink fan or thermal paste. The Noctua heatsink fans are not available easily here that I can see, although their thermal paste is, and I'm an Arctic Silver man when it comes to thermal paste. Old habits die hard. ;)

---

### Post by tokyobadger on 2016-01-15
> **Bucky Ball said:**
> The seller probably mentions the motherboards they use on the product details page but I don't read Swedish. :|
> **"Seller's website"]
[TABLE="class: productinfobox"]
[TR]
[TD="colspan: 3"]**Produkt-specifikationer**[/TD]
[/TR]
[TR="bgcolor: #c0c0c0"]
[TD="colspan: 3"][/TD]
[/TR]
[TR]
[TD]**Teknik**[/TD]
[TD][/TD]
[TD]CPU: Intel® Core&#8482 said:**
> 
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[TD]Processorkärnor: 4st (Quad-Core)[/TD]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[TD]Klockhastighet: 3400 MHz[/TD]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[TD]Max turbofrekvens: 4000 MHz[/TD]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[TD]Direct Media Interface (DMI3): 8 GT/s[/TD]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[TD]Cache: 8 MB Intel Smart Cache
[/TD]
[/TR]
[/TABLE]
Grundläggande logik: Intel® Z170 Express Chipset
Hmm - odd, the rest of my post disappeared. Just to chime in and say the specs are not too hard to read and that on the KDEnlive and OpenShot forums the consensus appears to be CPU speed not cores is what improves performance (currently). Neither of those apps has a hardware requirements list which I think they should address.

I don't edit video so I'll defer to someone who does to comment on RAM.

2nd Edit: just noticed that the motherboard chipset got cut out of the quote for some reason - it is a Z170 Intel Express

---

### Post by Bucky Ball on 2016-01-15
Thanks tokyobadger. I've decided on the 6700k, which is not a lot different, just a bit faster. ;)

---

### Post by tokyobadger on 2016-01-15
@Bucky Ball: in my original reply I commented that the i7-6700K being top of the Skylake tree would be the best option; I'd imagine with the right motherboard you could get a sensible overclock out of a good CPU to get a bit more performance in video editing apps.

I'm still running LGA1366 X58, i7-920 at 3.2GHz (up from 2.6) with 48G RAM (requires a slight overvolt) with SSDs and GTX680; nothing I've seen since I built it has enticed me to build a new system, I just wish Intel would have stuck with the LGA1366 platform a little longer, if they had I might have upgraded the CPU. 

[Just remembered this article](http://arstechnica.com/gadgets/2016/01/intel-skylake-bug-causes-pcs-to-freeze-during-complex-workloads/) about a bug recently discovered in complex workloads on Skylake - you'll also note that it's not the first such issue that Intel have faced. On the other hand, AMD are not (to me) putting out compelling alternatives.

Good luck and much fun with the new build :smile:

---

### Post by Bucky Ball on 2016-01-15
Says this later down the page, a little ambiguous, but implies the bug is fixable with a BIOS update:

> While this particular bug can be fixed via a BIOS update, we are reminded of another famous bug that plagued Intel's original Pentium processor that couldn't be so easily rectified.

Thanks again for the input. After going over it about a million times, I think its going to work, and I think I'm ready to jump. Just used my old desktop earlier and it is barely staggering along. That certainly gave me a little more impetus. Store opens again on Monday and I'll be there ... unless I come up with another bright idea.

Having said that, all suggestions welcome. 

I've dug around and there's nowhere I can get to build a machine with the same components anywhere near the cost of building myself so I'm resigned to doing it myself. No biggie, just other things to do at the moment.

---

### Post by Yellow Pasque on 2016-01-15
The bug should be fixable through a BIOS update or perhaps (eventually) through an updated intel-microcode package. I wouldn't worry about it too much.

The PSU is major overkill, so you can probably save a few $$ there. The only way you would need that much juice is if you seriously want to add another GPU, which seems unlikely if the CPU is going to be doing the heavy lifting for your editing. 500W or so should still leave you plenty of headroom for added disks, peripherals, etc.

I'm not familiar with the CPU cooler (haven't seen too much on this particular model on SPCR). Hopefully, you did your homework on it.

As for the GPU, I just got the Strix GTX950 a couple of months ago and it has been wonderful and quiet.

Good luck.

---

### Post by Bucky Ball on 2016-01-15
Excellent input and thanks Temüjin. The PSU was for future expansion, but doubt there will be any. You may have noticed that I am regularly barking on about efficient PSUs and not super-sizing so this has been irking me, indeed. I've plugged the component details into a few online PSU calculators and the majority of them came up with around 410W. One popped up with something like 765W, which had me a bit puzzled as I had a vague idea of what it should amount to (I came up with a figure closer to 400W also). Also had a bit of a question mark on how much a graphics card of this type is going to pull (will closer check wattage on all components and reconsider).

If 500W PSU is acceptable, that is good news. I have a 500W Green Power in my old desktop already. It is old but will do the job for now. I can then bung the Green Power (I think) 430W which has been sitting in an old box under my desk for five years in the soon to be old desktop.

Good news about the virtually silent Strix. I'm getting the OC model for the simple reason I can't locate the non-OC GTX 970 anywhere in town. I'm no overclocker (but we can't predict the future!).

Thanks again.

* About the Green Power PSU. Just dawned on me that, even though it is a good quality unit which will whirr away for years, it is about ten years old and I'm doubting it will have the correct connectors for the GPU or the CPU ... or the motherboard! Could be wrong. Again, will check thoroughly before proceeding. :-k

---

### Post by Yellow Pasque on 2016-01-15
PSU calculators generally overestimate power draw. The GTX 970 has a 145W TDP. The CPU is about 90W. Those are the major power drawers. Add another 40W for the rest of the system as a conservative estimate and you're at about 275W under load. Generally, you want a PSU that's about twice your max load (for best efficiency), and that's 550-600W as a really conservative estimate.
I realize there's more to a PSU than Wattage rating, but with a quality PSU, you shouldn't need to worry about the PSU make rinflating the Wattage rating and cheating on Amperage.

---

### Post by Bucky Ball on 2016-01-15
> **Temüjin said:**
> PSU calculators generally overestimate power draw. The GTX 970 has a 145W TDP. The CPU is about 90W. Those are the major power drawers. Add another 40W for the rest of the system as a conservative estimate and you're at about 275W under load. Generally, you want a PSU that's about twice your max load (for best efficiency), and that's 550-600W as a really conservative estimate.
I realize there's more to a PSU than Wattage rating, but with a quality PSU, you shouldn't need to worry about the PSU make rinflating the Wattage rating and cheating on Amperage.

This is what I imagined was going on. ;)

* Although,[ this page]("httphttps://www.asus.com/au/Graphics-Cards/STRIXGTX970DC2OC4GD5/specifications/") states this about the Strix GTX 970 OC:

> Power Consumption: up to 225W1 additional 8 pin PCIe power required

Brings it the 320W for CPU/Vid. Not sure what '8 pin PCIe power required' means.

---

### Post by Yellow Pasque on 2016-01-15
> **Bucky Ball said:**
> Not sure what '8 pin PCIe power required' means.

It means your GPU needs more juice than the PCI-e slot itself can deliver. Most PSU's you can buy will have at least one PCI-e connector, probably in 6+2 form:
[http://www.playtool.com/pages/psuconnectors/connectors.html#pciexpress8](http://www.playtool.com/pages/psuconnectors/connectors.html#pciexpress8)
[http://www.playtool.com/pages/psuconnectors/connectors.html#pciexpress6plus2](http://www.playtool.com/pages/psuconnectors/connectors.html#pciexpress6plus2)


> Brings it the 320W for CPU/Vid.
That seems about right (or maybe a tad high). From the reviews I just looked at, systems with a GTX 970 seem to be pulling 300-350W from the wall under full load. I'd be very comfortable with a 550W PSU, though you could get away with less and maybe save a bit of power with a 600/650W model. Cooler Master makes some 550W PSU's. Since you prefer the brand (or maybe it's the best thing your vendor carries), one of those would seem ideal. The G550M is guaranteed Skylake-compatible and guaranteed to have enough juice to power an Nvidia Titan. Their GM series seems like a good mix of price, Amperage, efficiency and features.

---

### Post by Bucky Ball on 2016-01-15
I save myself a dollar with [this]("http://www.msy.com.au/nsw/hurstville/power-supply/14465-antec-edge-550-550w-edge-80plus-gold-full-modular-gaming-power-supply-unit.html"). Five years warranty and 80+ gold (up to 92%) make this viable for me. Can't find anywhere if it's 'Skylake ready' but says it's ready for Haswell (Update: apparently 'Haswell Ready' is fine; tokyobadger mentioned a bug earlier with a link but seems a BIOS update will fix). 

I use [this store]("http://www.msy.com.au/nsw/hurstville/84-550w-625w") for a couple of reasons: they are always the cheapest in town (even if it's by a dollar on some items) and they have (generally) the largest range (although the xmas splurge seems to have cleaned them out, this can change literally overnight as they re-jig their stock levels on the website daily). So they only have one GM series model at the moment.

Cast your eye over the PSUs there and see if you spot something else I haven't with your expert eye ... ;)

PS: Yes, I like Coolermaster, but have actually used mostly Antec in the past so good with that. Main thing is its a solid, efficient unit, 80+ and preferably gold, regardless of what I end up with. :)

---

### Post by J_Me on 2016-01-16
@Bucky Ball From the link to the case your interested in [http://www.coolermaster.com/case/mid-tower-silent-series/silencio452/](http://www.coolermaster.com/case/mid-tower-silent-series/silencio452/) The picture shows a water cooled heatsink covering the CPU which isn't included with the case(I believe). You'll need one of these.[br]1[/br] [http://www.newegg.com/Water-Liquid-Cooling/SubCategory/ID-575](http://www.newegg.com/Water-Liquid-Cooling/SubCategory/ID-575)[br]1[/br] [br]1[/br] Or maybe one of these type of things could fit(depending on availability/cpu brackets/case)[br]1[/br] [http://www.newegg.com/Product/Product.aspx?Item=N82E16835608045](http://www.newegg.com/Product/Product.aspx?Item=N82E16835608045)[br]1[/br] [br]1[/br] Generally speaking the bigger the fan the quieter it will be.

---

### Post by Yellow Pasque on 2016-01-16
If silence is what you're after, You may want to keep an eye out for a Corsair RM550x. The Antec Edge didn't seem to impress the SPCR crowd. I don't have much time right now to research anymore (working 12 hour shifts).

---

### Post by Bucky Ball on 2016-01-16
> **Temüjin said:**
> If silence is what you're after, You may want to keep an eye out for a Corsair RM550x. The Antec Edge didn't seem to impress the SPCR crowd. I don't have much time right now to research anymore (working 12 hour shifts).

Understood and thanks. Yes, silence is my thing. :) 

Still digging away here. Am seriously thinking about going for the Strix 950 instead of the 970 also. From the research I've been doing, and for my purposes, the difference is negligible, although there is one. The 950 has a lot going for it, though. Less power required and price for two. They are both ultra-quiet (have the same 'no fan til 67 degrees' technology) so nothing in it there. 

Also thought about downgrading the MB. As this is not intended for gaming, I don't need something with that much expandability. My requirements, though, are that the MB is ATX and can handle DDR4. At the moment, the ASrock K4 Gaming MB is the only one, at that store, that has both. I'll keep digging. 

Thanks again. ;)

---

### Post by Bucky Ball on 2016-01-19
For those of you that are still with me, I have just emailed the parts list attached to this post to a store here and they are going to get back to me with their best price, considering I'm buying the whole rig from them. 

My final tally in attached screenshot comes to about $200 more than I was hoping to spend, so fingers crossed. The end result will do me good service now and in to the future, though, so keeping that in mind. This is the hardware I want to be using, I have the cash at the moment, although its a squeeze, so why not? :-k

Anyone notice anything that is unfriendly or noisy? I've done my best to keep it as quiet as possible with my budget. Quieter the better (both for audio/video editing and because I am sensitive to ambient noise levels).

---

### Post by Bucky Ball on 2016-01-27
For anyone that's interested, here it is. Ordered and they're building as, frankly, I spent too much time researching and with fieldwork starting Monday don't have the time to do it myself. Too much else to prepare.

Asus Strix GTX 970
Intel i7 6700
Fractal Design Define R4
Thermaltake Toughpower Gold 650w
Gigabyte H170-HD3
Kingston Hyper Fury DDR4 16Gb
Coolermaster Hyper 212x CPU cooler

One thing I'd completely overlooked, and no-one told me about, was that the H170 motherboard is for the locked 6700 and the z170 for the unlocked 6700k. Almost wasted some time and money there by going for the 6700k and the h170 MB. Thankfully, it popped up quite by chance during my research. I have no intention of overclocking so saved a bit on motherboard and CPU there. 

So, dropped back a little on the processor but this is going to cope without issue with my meagre needs and rendering times should be fine. Wish me luck and will report on the noise level/performance in about a week. 

Now that's out of the way I can devote 100% focus to other things. Cheers. :)

---

### Post by tokyobadger on 2016-01-27
Congratulations on the purchase and well-done on catching the H170 limitation. Fully empathize with the situation on not building yourself. When I was younger I'd regularly tear down my boxes to clean them out, redo wiring, redo CPU cooling. These days I just don't find the time. I think the next build may be the last if I don't cave and go Build-To-Order.

Thank you for sharing the pre-purchase research and dilemmas - having not built for a long time, it's been very informative to follow along. Here's to a smooth install (16.04?) and much fun using the new build (apologies, it's a Chilean red, not a an Australian one)

---

### Post by Bucky Ball on 2016-01-27
Cheers for that. Yea, well, I've just been thinking about which release to install. I generally install a supported LTS minimal and take it from there, but there is an Xubuntu-minimal as of 15.10 ... but maybe straight for X-mini 16.04 LTS and take a risk? Can't afford breakage once stable, though ... 

I was going to drop the current SSD in and all should work but dawned on me it is 32bit install for a 32bit machine. Don't want that for the new one so time to start again.

And also coincidentally (are you reading my mind?) I've just been moping about the fact I'm not building this one. Almost regretting it. Remembering the satisfaction of sitting in the driver's seat of your new build. I'll be wondering if that rubber grommet is under the PSU ... With that case, though, should be virtually silent regardless compared to what I'm used to (and one of the reasons I don't use that old banger much anymore).

Roll on delivery time. I'll have started the fieldwork when it arrives so it will be install and straight to work when it does.

---

### Post by gordintoronto on 2016-01-27
I'm happy with Xubuntu 15.10, and planning to upgrade to 16.04 when it becomes available.

It sounds like you have not made a final choice for video editing software. I'm a big fan of Cinelerra, in part because of the excellent tutorials at this site: 
[http://www.g-raffa.eu/Cinelerra/HOWTO/](http://www.g-raffa.eu/Cinelerra/HOWTO/)

There are also tutorials on other sites.

The downside to Cinelerra is that you really need to spend an hour or two on tutorials and setup before you try to edit any video. Think back to when you first edited audio: was it any different?

---

### Post by Bucky Ball on 2016-01-28
Well, I have a reasonable handle on video editing (much of which could be easily refreshed in an hour or two) and used Cinelerra back in a day when it was probably more klunky than what it is now. I don't really need to go that far for what I'm doing here, though.

Kdenlive looks like it might do the job. My main issue is de-fisheye-ing the footage which I will probably do in Windows as, although possible in Blender, looks like it might take a while to get my head around (never used Blender). See how it goes, though, as have been checking a vid on how to turn Blender into a video editor without too much trouble. That would cover editing the video and audio together and defishing the footage all in the same program.

Ideally, that is what I am looking for. Can Cinelerra defisheye vid footage now days?

How much time I've got to get my head across the software will probably determine what I use to a large degree. Had a quick look before starting on the build but started getting more serious about the soft-side today actually. ;)

---

### Post by Bucky Ball on 2016-02-04
A final note on this: I'm typing to you from the new build! And it rocks. Very fast, quiet and cool and appears to chew through the footage I'm shooting just fine. Haven't started editing and rendering as yet, so the real test is yet to come, just viewing the 'rushes' as they come; MP4 in VLC.

Decided on Xubuntu-core 15.10 because, well, I was in a rush, wasn't sure how 14.04 LTS would go with newer harder and 16.04 LTS is not yet released and officially supported. The latter was tempting as I stick with LTS releases generally, but I'll live with an odd feeling using an interim release for 'serious' stuff rather than one of impending doom using an unsupported, unreleased one!

Oh, well. Having a few niggling issues but the stuff of other threads. So far so good, the box will do the job fine, ticks all boxes to this point. The final parts I posted (plus a couple or three Western Digital Blacks :)) are a suitable combo for editing 1080p video and 48/24 audio and will last awhile. :D

(PS: Still trying to figure out the software side of it. Blender has a video editor, seems to be working fine, though can't get it to play with Pulseaudio so currently installing jack. It has settings for OpenGL, the GPU does too, the driver for the 970 was in Additional Drivers and despite not being the latest it works fine. 

Need nothing more than Audacity for mixing and exporting the audio from the Zoom H6 recorder and then hopefully bring it all together in Blender. At least that's the plan! A steep learning curve so flat-out and loving it.

---

### Post by Yellow Pasque on 2016-02-04
What's the loudest component? Is it the PSU fan?

---

### Post by Bucky Ball on 2016-02-04
> **Temüjin said:**
> What's the loudest component? Is it the PSU fan?

Yep, and that's barely audible. The case fans are about the same volume. They have a low/med/high switch. They are on medium. When I switch them to low, no difference. When I put them to high, you can hear a slight increase in volume.

It is, of course, not completely silent, but compared to the jalopy I had, it is golden quiet bliss. Put it this way, you forget it is there until you switch the machine off. I will mention that the machine is on a workbench probably two foot from my left ear. 

If it was under my desk don't think I'd hear much at all. :)

---

### Post by tokyobadger on 2016-02-06
Congratulations on the new box and good to hear you're happy with it. I'm sure you'll get the niggles resolved soon enough.

We're  close enough to 16.04 that a few weeks on 15.10 is pretty much a  temporary solution. I'm actually using 16.04 as my daily OS and it has  to be one of the smoothest development cycles I can remember.

---

### Post by Bucky Ball on 2016-02-06
Thanks for the input. Yep, everything purring now. I have a backup routine worked out and have chucked a couple of WD blacks in there also. 

Recording video and audio separately so ... video and audio goes to one external backup drive at the end of each shooting day, the audio goes separately to one WD black, video to another. I'll get another black next week and use that for projects/scratch disk. It's a plan!

System itself is running wonderfully and so's Xubuntu-core (now I have a couple of very weird niggles out of the way). :D

---

### Post by Bucky Ball on 2016-02-18
Just thought a final word here might be appropriate to tie the story up, and because I'm excited!

So, I went with Blender to do the job, aided by Audacity. Last night I sync some audio from the Zoom H6 audio recorder with 1920x1080 HD footage from the camera using Audacity, used the camera sound track as a 'template' to snip the synced Zoom audio so both tracks were exactly the same length. I then opened the camera track in Blender, then the doctored Zoom audio, deleted the camera audio. Frame count matches perfectly, plays glitch free and looks and sounds fantastic.

I then attempted and achieved snipping each end, leaving me with 00:01:05 to be used as an example in the final submission of my fieldwork research. Rendering to .avi took about 00:01:20.

I will add that the setup has been complemented by three WD Black 7200 1Tb drives, so that with the SSD is all pretty quick. Backing up 20Gb from the camera to the drive takes some time, but from drive to drive, very quick.  

Needless to say, my brain hurts from the Blender learning curve at night and fieldwork learning curve during the day, but happy as a pig in the proverbial. :D
_____

Conclusion: Yes, my final hardware list works fine for video editing and Blender is a hugely powerful, partly tame-able, media editing monster which will do the job if you have the time and patience to get across it (and I'm baby-steps, a long way off). There are some excellent first-step how-tos for video editing on Youtube, and probably for all the other things it can do, too.

Thanks everyone that chipped in with their thoughts, advice and feedback.

@tokyobadger: re. 16.04 LTS, I installed it on another partition four or five days ago and took about an hour to install and set up identical to the 15.10 install. I'm used to using the mini.install so xubuntu-core is a bit of an indulgence to start! Point being, I need very little installed to do this particular audio/video job for the month. After 16.04 install I did one 'sudo apt-get install' line and then it was the keyboard shortcuts and pretty much done. 

So when 16.04 LTS is released I intend to simply swap to that partition. It's working fine right now and I sometimes use it to back up the camera and Zoom and have a general sniff around when I get home. :)

---

### Post by tokyobadger on 2016-02-18
@Bucky Ball: great to hear you're humming along with the new set-up. Starting to feel the itch when I re-read this whole thread ... and bonus time is coming soon ... at minimum I'm getting a new mouse, this one is driving me nuts (in fairness it's 7 years old and has moved internationally 3 times)

Re: the 16.04 install, I run multiple distros (currently all Debian-derivatives) across 3 SSDs but I'm spending most of my time in 16.04. Good to hear it's working for you, recently I've been seeing "new software for new hardware" as a popular solution for hardware issues with older releases

Have fun :-)

---

