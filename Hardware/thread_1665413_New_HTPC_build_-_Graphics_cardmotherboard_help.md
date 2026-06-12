---
title: "New HTPC build - Graphics card/motherboard help"
date: 2011-01-12
forum: Hardware
---

### Post by el_Paraguayo on 2011-01-12
(This was originally posted in [AVForums](http://www.avforums.com/forums/home-entertainment-pcs/1392800-linux-new-htpc-build-motherboard-graphics-advice-needed.html) but they said they're not so hot on Linux so I've turned to the people that are. The comments about reading through existing threads applies as much to this forum as AVForums.)

A year ago, I installed Mythbuntu on my parents' old Dell Dimension. It worked a treat (my wife never misses her US teen dramas) but the 20gb hard disk doesn't go far. Also, using Handbrake to convert to MP4 to put films on my phone was *painfully* slow.
 
So, time for a new machine.
 
I've been trawling Google and Forums for the last fortnight and this place seems to be the right place to go. I've learnt a lot so far, but I need some more help.
 
My old PC is in an Antec Sonata silent case which I intend to use. (The stock CPU cooler is the only noisy bit - but I can't find many Socket A silent coolers now).
 
In any case, I'm looking for something a bit beefier to plug into my TV.
 
My plan is to have the machine as a MythTV backend and XBMC frontend (I'll also have music and photos on the machine). This does mean that machine is likely to be permanently on.
 
The main things I'm stuck on are the Motherboard and graphics card.
 
**Motherboard:**
The Antec is a full ATX case so I'm not concerned about the size.
 
*On-board video:* Can't work out whether this is better or not. TV has VGA/HDMI in so I'll need those.
I don't have any HD content (yet) but want to future proof as much as possible.
I've read that NVidia is better on Linux than ATI - but most onboard video seems to be ATI.
 
*Audio:* My audio system has a spare optical in which I can use (or would HDMI+Audio into my pass through to audio receiver?)
 
*PCI:* I've got a PCI TV tuner which works with MythTV which I plan to recylce.
 
Looking at this card at the moment:
[ASRock AM3 M3A770DE/A/ASR]("http://www.amazon.co.uk/ASRock-M3A770DE-Motherboard-Socket-5200MT/dp/B002LFYYAY/ref=sr_1_5?ie=UTF8&qid=1294760011&sr=8-5") 
I don't have any preference for manufacturer.
 
**Graphics Card**
As said above, I am looking for NVidia chipset but I've read that some hardware ( G98 ) has trouble with H264 video.
 
As the machine is going to be in my front room - I'd prefer a silent card.
 
**CPU**
The [AMD X2 240e]("http://www.amazon.co.uk/Processor-Athlon-Energy-Efficient-Socket/dp/B002PA7U88/ref=sr_1_2?ie=UTF8&qid=1294750747&sr=8-2") looks good to me. I presume that it would have enough juice for HD video.
 
**Cooler**
Having had a bad experience with stock coolers I'll aim to get something quieter - something like the [Shuriken]("http://www.amazon.co.uk/Scythe-Shuriken-SCSK-1000-Processor-cooler/dp/B0015SYT6C/ref=sr_1_4?ie=UTF8&qid=1294750852&sr=8-4").
 
**Memory**
About 2Gb - or do I need more?
 
**Drives**
Main drive 150Gb - OS/photos
Second drive 1Gb - music/videos/TV recordings
 
 
 
I'd love to hear people's comments/recommendations especially in terms of motherboard and graphics card.
 
 
Lastly, will I have any issue in terms of connecting the HTPC to a TV via HDMI if the PC is permanently on - i.e. will there be a handshaking issue?
 
 
Many thanks for your help.
 
elP

---

### Post by Joe of loath on 2011-01-12
As a reference, here is my most recent build, it works perfectly on 10.04.

[https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?Id=599084edb9ee46d69c651b9442e18ffe](https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?Id=599084edb9ee46d69c651b9442e18ffe)

I also unlocked the 4th core on the processor in the BIOS, although it only works on some chips.

---

### Post by el_Paraguayo on 2011-01-12
Thanks. Looks like a nice set-up.
 
The graphics card is a bit on the expensive side. Also, as this will be an HTPC in my front room I'd be inclined to go for a passively cooled one if possible.

---

### Post by Joe of loath on 2011-01-12
You say expensive, I say 'futureproof' :lol:

It's actually very quiet; it's controlled by a temperature sensor on the chip, and I can hardly hear it.

For a passively cooled one you're going to have to look at a much lower spec. Probably not a problem, the card we have is a gaming one.

---

### Post by cascade9 on 2011-01-13
GPU- Get nvidia. Onboard video is OK these days, but for AMD is mostly ATI and ATI hardware video decdoing (XvBA) is buggy. nVidia hardware video decdoing (VDPAU) works really well. You can get nVidia onboard vide, but I've never been that impressed with teh new nVidia chipsets,, I think AMD chipsets and a cheap nVidia card is the way to go. 

GT210, GT220, GT430. Cheap, good VDPAU support, passive models avaible.  

CPU- 240e should decode HD without VDPAU just fine (but VDPAU is a better idea than CPU HD decoding). Nice cool little chip. 

Heatsink/fan- Why a Shuriken SCSK-1000? They are made for 'slim' cases normally, though its an interesting heatpipe/traditional heatsink setup. Heatpipes tend to work better over 50c, so if you wanted a passive (fanless)/semipassive system with low CPU temps it might be a good one.

RAM- 2GB would be fine.

Drives- 150GB? *blinks* Unless its an old Hdd you are recycling in the system, dont. I'd also go for a 2TB 2nd drive over 1TB, its amazing how fast you fill space. 

Motherboard- Asorck M3A770DE/A/ASR- Avoid! Besides there being no listing for that exactl model nmber on teh asrcok website, its also got a VIA 1708S sound chip- widely known as bloody awful (and poor linux support into the bargin). 

I'd go for the Gigabyte 870A-UD3 you posted on AVforums myself. If you want to save a little money, make sure you get AM3 (not 'AM2+/AM3'), and the newer chipsets (870, 890FX) have a ew advantages over the older chipsets (SATAIII support in particular). 

870- good base model, overclocking (and underclkcing) capable.

890FX- 'top end' model, slightly better overclocker/underclocker, tends to have more 'features' (some of whihch tend to be useles with linux), better cooling.  
> **Joe of loath said:**
> As a reference, here is my most recent build, it works perfectly on 10.04.

[https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?Id=599084edb9ee46d69c651b9442e18ffe](https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?Id=599084edb9ee46d69c651b9442e18ffe)

I also unlocked the 4th core on the processor in the BIOS, although it only works on some chips.

I had a look at that, and I was a little shocked....I've never been an MSI fan, but that '870-C45' motherboard has got to be one of the most misleadign part numbers I've ever seen in my life... '870' is the newer AMD chipset, but MSI gave the '870-C45' an older 770 chipset? Thats just crap...

---

### Post by el_Paraguayo on 2011-01-13
> **Joe of loath said:**
> You say expensive, I say 'futureproof' :lol:
Very important - as I found while trying to find a new cooler for a Socket A board... 
 
Cascade: Thanks so much for your tips.
 
In answer to your questions:
 
**GPU** - I thought NVidia would probably be the way to go - will look to see what I can find. 
 
**Heatsink** - Doesn't need to be the Shuriken - I've just had bad experiences with stock AMD fans (it's the one thing that makes a noise in my silent case). 
I've no idea how hot the 240e will get - given it's a low voltage cpu, hopefully not too hot.
I'm always slightly concerned by passive coolers on CPUs but that could just be my inexperience showing!
 
**Drives:** Yes, the 150Gb is a recycled drive. If this is a bad idea I'm happy to buy an extra drive.
Is my idea of having the OS on one partition and audio/photos on another on that drive appropriate?
 
**Motherboard:** Great advice. Thanks.
 
 
Looks like I'm almost there.
 
I'll have to document the build/software installation as a tutorial (if I don't screw it up) and post on the forums as a thank you.

---

### Post by cascade9 on 2011-01-13
HDD- 150GB isnt bad, its just bad to buy one now. Sure, if its just for the OS and /home you dont need any more, and even 150GB is more than a lot (most?) people would need in that situation. 

BTW, if its 150GB IDE, I would consider getting a SATA drive. The newer 870/SB850 chipset doesnt have a PATA controller, so manufactuers tend to add PATA controllers. Some of them are dodgy with linux. 

I'll revise my GA-870-UD3 to GA-870UD3P (no PATA and less onboard junk), if you have an all SATA HDD/optical setup or are prepered to get the parts you need to have that. Less stuff you dont really need, and personally, I've found that 'vanilla' boards run better than boards with a ton of extras. 

The early 'factory' heatsink and fans from AMD weren't great. hey are better now, but the very fact you've said 'passive' makes me think that you migth perfer a better one..and they arent that expensive these days. 

Passive cooling a CPU is possible, but unless you've got a very low heat CPU its risky. The 240e should run pretty cool, but I dont think it would be cool enough to run totally passive. Though if you are using a 120mm exhaust fan on the solo, its close enough that it could let the CPU survive without any major issues. 

A nice heatsink/fan to check out is the noctua NH-U12P (great heatsink and fan). Virtually silent at low fan speeds, and it will keep the temps very low at low fanspeeds as well. Win/Win. 

If you are after quiet, have a look at the seasonic x-650 gold. Expensive power supply, but great quality. They run totally fanless at low loads, but if the load/temps ramp up the fan kicks in (so its as quiet as a fanless power supply at low loads, but will spin up the fan if things get hot....great idea)

[http://www.silentpcreview.com/Seasonic_X650](http://www.silentpcreview.com/Seasonic_X650)

Since you're in the UK (I assume) try staticice for good prices- 

[http://www.staticice.co.uk/](http://www.staticice.co.uk/)
 
BTW, I forgot- you can still get socket 'A' coolers, but yeah, they are hard to find. Some of the newer CPU coolers can be modded to fit a socket a (just use the clip from a socket a cooler to hold it down) but actually knowing what is modable or not isnt easy.

---

### Post by el_Paraguayo on 2011-01-13
Cascade: again, some fantastic advice.
 
Yes, I am in the UK.
 
I've had a look at those graphics cards: Some interesting reviews around - not entirely flattering. The trouble is, most reviews are for hardcore gaming which just isn't what I'm after.
 
My main concern is with noise/cooling - most cards seem to have a fan on and I really don't want the noise. However, if I go (and can find) passive card then I'd need to be happy that the case is well ventilated. The case has a large fan on the back which sucks air through the case (ventilation holes on the sides at the top - not near expansion slots).
 
Can't believe how much of headache this can be!
 
Will persevere though - I *know* I'll get there eventually.

---

### Post by el_Paraguayo on 2011-01-13
In answer to your other questions:
 
yes 150Gb drive is SATA.
 
Another reason for the Shuriken was that it's an upright case, so I'd be concerned about the weight of a large cooler creatin stress on the CPU or board.
 
The case's PSU (350W) is pretty silent so I'd not look to replace that unless necessary - your recommendation looks very nice though!

---

### Post by cascade9 on 2011-01-13
Thnaks ;) 

The gaming sites tend to give the GT210/GT220/GT240/GT430 a nasty reviews...but they always give 'low end' cards nasty reviews. For a HTPC, the gaming cards are NOT a good idea. TDP (termal desing power) on a GT210, 30.5watts, GT220, 58watts, GT240, 69watts, GT430, 49/60watts (retail/OEM). A GTX460, the current mainstream favourite from nVidia for gaming, 150-160watts. 

Extra heat = more fans blowing to exhaust the heat (or fans spining faster). Not good for a HTPC. 

BTW, actual power consumption will be below the TDP figures, have a look here- 

[http://www.xbitlabs.com/articles/video/display/gpu-power-consumption-2010_3.html](http://www.xbitlabs.com/articles/video/display/gpu-power-consumption-2010_3.html)

A Gt210 should do everything you want, if you are nervious then get a GT220. I'm runnign a card with less power than a GT220 (8600GT), iot does VDPAU nicely. No desktop issues either. Passive models are around. If your having trouble finding which models are passive cooled, then you can go to newegg-> video cards-> advanced search-> select "GPU- G/GT series" and "cooler- fanless".

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600007321+600029795&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600007321+600029795&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

That wont show you all the pasive cooled GT models, but it will give you a some to choose from. Finding them in the UK should be as easy as entering the model number into staticice. (eg, EN210)

I actually own an antec solo  as well. Phenom II 550 with factory heatsink/fan (dual core, 80watts TDP, nearly twice the TDP of the 240e), 8600GT (pasive cooled), corsair HX20 power suppkly, stock rear fan. Never overheated, and I've only bumped the fan from 'low' to 'middle' for summer. Its run in well over 30C with no issues.  

With the fan on 'low' its near enough to silent.

---

### Post by el_Paraguayo on 2011-01-13
Found this site about compatible cards too:
[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)
 
I think 220 might be the way to go.
 
 
Thanks for all your help so far. I owe you!

---

### Post by cascade9 on 2011-01-13
Yeah, a GT220 migth be the safer choice. 

I forgot- with the neat backplates that heatsinks use there days, wieght and size is far less of a concern than it was in the past. I know people who use bigger heatsinks than the noctua NH-U12P, cart them around to LAN games at times, and havent had any issues. I can see why you would worry though. 

> **el_Paraguayo said:**
> Thanks for all your help so far. I owe you!

Nah! I'm always poking hardware sites, its nice to be able to help somebody out with the semi-useless knownledge I have.

---

### Post by el_Paraguayo on 2011-01-13
> **cascade9 said:**
> Nah! I'm always poking hardware sites, its nice to be able to help somebody out with the semi-useless knownledge I have.
And I can blame you if it all goes wrong!
 
I'll put together my shopping list and post at the weekend.

---

### Post by cascade9 on 2011-01-13
> **el_Paraguayo said:**
> And I can blame you if it all goes wrong!

*hides* 

Nobody here but us chickens!

---

### Post by el_Paraguayo on 2011-01-13
> **cascade9 said:**
> ...Finding them in the UK should be as easy as entering the model number into staticice. (eg, EN210)
Although I had said I'd go for the 220, having read around more the 210 is getting some good reviews.
 
The EN210 looks pretty nice too - but you already knew that, didn't you?!

---

### Post by cascade9 on 2011-01-14
I havent seen the EN210, so its hard to say. I wasnt at all impressed with the silent asus 8400GS my housemate bought, it runs a lot hotter than the silent 8600GT I'm running (and the 8600GT should be hotter). 

It should be fine, I'm just getting more and more wary of asus as time goes on.

---

### Post by el_Paraguayo on 2011-01-20
Wow, who knew it would be so hard to find a GPU?!
 
Currently looking at:
 
[Sapphire ATI HD5450 1GB GDDR3 PCI-E HDMI Fanless]("http://www.quietpc.com/gb-en-gbp/products/vga-cards/sap-hd5450")
[MSI N210-MD512H Fanless NVIDIA N210 512MB GDDR2 HDMI]("http://www.quietpc.com/gb-en-gbp/products/vga-cards/msi-n210-md512h")
[Zotac Fanless GeForce GT430 1GB DDR3 ZONE Edition]("http://www.quietpc.com/gb-en-gbp/products/vga-cards/zo-gt430")
 
The Zotac is the highest spec NVidia card so I'd like to go for that but there's one issue that I'm not sure about:
 
I've read about people who connect their HTPC to their TVs via HDMI having to reboot the PC to get the TV to recognise the signal. 
 
Is this a common issue? My machine is likely to be permanently on so this is a big issue for me.
 
 
As for the other cards - the HD5450 looks nice and there's a guide for getting ATI cards to work with MythTV (see [here]("http://www.mythtv.org/wiki/ATI_Radeon_HDMI")) so I'm not so terrified by using ATI over NVidia.

---

### Post by cascade9 on 2011-01-20
ATI- the problem is hardware video decdoing. XvBA is buggy. VAAPI works, but its still not as good as nVidia VDPAU. 

You can get that HD 5450 for less than your link..quite a bit less. 

[http://www.tekheads.co.uk/product/Sapphire-ATi-Radeon-HD5450-1GB-DDR3-DVI-HDMI-VGA-PCI-E-Graphics-Card-Retail_25637.html](http://www.tekheads.co.uk/product/Sapphire-ATi-Radeon-HD5450-1GB-DDR3-DVI-HDMI-VGA-PCI-E-Graphics-Card-Retail_25637.html)

I wouldnt touch that Zotac. Besides being overly expensive (you can get a GT240 for less) its not even using the nVidia specs. Its using DDR3, nVidia specs GDDR3 for the GT430. 

I have no idea how common the TV/HDMI problem is, but if you run 24/7 you shouldnt get it. Just make sure that the TV is turned on when you boot (or reboot), then it wont matter if you turn the TV on or off, the EDID (etc) settings are all there.

---

### Post by el_Paraguayo on 2011-01-20
Cascade - you have the patience of a saint, calmly replying when you're probably pulling your hair out at some of my suggestions!
 
Ok, so I either go for the cheap GT210 or dish out for a GT240 like this [Asus]("http://www.amazon.co.uk/gp/product/B003D1NBVS/ref=olp_product_details?ie=UTF8&me=&seller=").
 
Time to check the bank...

---

### Post by cascade9 on 2011-01-20
> **el_Paraguayo said:**
> Cascade - you have the patience of a saint, calmly replying when you're probably pulling your hair out at some of my suggestions!

After seeing (literally!) people come to blows over video cards, this is farly sedate. :lolflag:  

After having a look around, I withdraw my 'silent GT240' recommendation. Seems like all the models I can find are using DDR3, and that has a nasty performance hit. See here if you want gory details- 

[http://www.anandtech.com/show/2906/1](http://www.anandtech.com/show/2906/1)

That would only really matter for gaming, but if you arent gaming then GT430, GT210, GT220, GT240, meh, wont make any real difference.  

So I'd go for a GT210 or GT220. Thats just me, I'd understand if you went for the GT430 or a AMD card.

---

### Post by el_Paraguayo on 2011-01-20
Absolutely no interest in gaming (unless I do some really old school emulator...) so looks like the GT210 should do nicely.
 
Time to open the wallet and get building.

---

### Post by cascade9 on 2011-01-20
Good luck on your build! ;)

---

### Post by el_Paraguayo on 2011-01-20
One last thing - the case has mounts for an internal 120m fan which points at the GPU - so I'll be using this to keep air moving round the GT210.

---

### Post by cascade9 on 2011-01-20
The rear 120mmm fan is meant to be an outtake fan, not an intake. Because of the way that air flows into and around the case, it works better that way. 

The GT210 has a heat output of sod-all anyway. Even a passive cooled GT210 shouldnt get to hot.

---

### Post by el_Paraguayo on 2011-01-20
This is a fan that sits inside the case behind the HD bays - the idea is it sucks in some air through the front and blows it onto the PCI slots.
 
Given it's likely to only be about £15 for a silent fan and the machine will be permanently on I think it might be worth doing - but I suppose I can just fire it up and see how hot it does get.

---

### Post by cascade9 on 2011-01-21
I'm running a hotter setup than that, in a hot enviroment. Adding a front fan does make things cooler, but I'm a long way from dangerous temps. I'd really doubt that you'd need a front fan. ;)

---

### Post by kco1196 on 2011-01-21
I bought the Asus GT430 w/fan.  It's so quiet you can hear a cricket fart in the neighbors yard.

---

### Post by el_Paraguayo on 2011-02-11
Quick update (if you're still reading this):
 
Build the machine yesterday - installation of mythbuntu was easy. Graphics card worked out of the box. 
MythTV configured (although migrating the old database to the new machine was painful).
 
Now just need to copy music and photos onto the machine then configure lirc before setting up XBMC. Simples.
 
Booting is fast. 
 
Machine is silent.
 
Very happy.
 
 
I'll be putting together more detailed descriptions of the installation/configuration on this site: [http://ubuntuhtpcbuild.wordpress.com/](http://ubuntuhtpcbuild.wordpress.com/)

---

### Post by cascade9 on 2011-02-11
Good to hear your are happy with the build. (and thanks for the thanks on your link) ;) 

Happy mything!

---

### Post by el_Paraguayo on 2011-02-16
I've come across a couple of issues. One seems to be hardware, the other software (I think).
 
Hardware
 
The PSU seems to be running quite hot. By that I mean that the air coming out the back is hotter than when the case ran my old XP setup. I'm not sure what the standard operating temperature is, but I don't really want it running hot if it's going to be on so much or when I'm not in the house.
 
Am wondering whether it's because the PSU isn't powerful enough for my setup - it's 350W - but I don't know how to determine my power requirements. (EDIT: According to [this site]("http://www.antec.outervision.com/PSUEngine"), I should only need about 265W)
 
The air coming out of the case fan is nice and cold.
 
Software
 
Mythbuntu won't shutdown the PC - it seems to stop services, unmount drives etc. but won't power down. Is there any way to debug why it's not - e.g. particular logfile?
 
Thanks.

---

### Post by cascade9 on 2011-02-16
> **el_Paraguayo said:**
> I've come across a couple of issues. One seems to be hardware, the other software (I think).
 
Hardware
 
The PSU seems to be running quite hot. By that I mean that the air coming out the back is hotter than when the case ran my old XP setup. I'm not sure what the standard operating temperature is, but I don't really want it running hot if it's going to be on so much or when I'm not in the house.

Am wondering whether it's because the PSU isn't powerful enough for my setup - it's 350W - but I don't know how to determine my power requirements. (EDIT: According to [this site]("http://www.antec.outervision.com/PSUEngine"), I should only need about 265W)
 
The air coming out of the case fan is nice and cold.

This is where you hit problems with older PSUs. I'll try to make this as non-technical as possible ;) 

The 'problem' is that the wattage isnt just from a single voltage. All ATX PSUs deliver 3.3v, 5v, and 12v (there is also -3.3v, -5v,-12v and +5vSB as well, but they are normally pretty low wattage so not worth worrying about)

So when you see a PSU rated at 'XXX watts', its actually made up of AAA watts on the 3.3v rail, BBB watts on the 5v rail, CCC watts on the 12v rail. 

Now where things get complicated is....hmm, easier to quote wiki than to try to say it myself- 

> When high-powered GPUs were first introduced, typical ATX power supplies were "5 V-heavy", and could only supply 50–60% of their output in the form of 12 V power. Thus, GPU manufacturers, to ensure 200–250 watts of 12 V power (peak load, CPU+GPU), recommended power supplies of 500–600 W or higher.


 More modern ATX power supplies can deliver almost all (typically 80–90%) of their total rated capacity in the form of +12 V power.


 Because of this change, it is important to consider the +12 V supply capacity, rather than the overall power capacity, when using an older ATX power supply with a more recent computer.


[http://en.wikipedia.org/wiki/Power_supply_rail](http://en.wikipedia.org/wiki/Power_supply_rail)

I would guess that the last computer you ran on the 350watt PSU was older. If its power requirements were anything like yoru new system, then your last computer was usign more of the 5v rail, and less 12v rail.  

Because you are pushing the 12v rail much harder, its closer to the limit, so outputs more heat. 

Its _probably_ still safe, but I understand your caution. Who wants to burn down the house becuase of $100 or less worth of PSU? 

At least you know that the CPU and GPU are running nice and cool (or else the case exhaust fan would be hot, not just the PSU exhaust fan). ;) 

BTW, power supply calculators are at best an 'educated guess'. Here is  great article on how much power systems actually need (yes, there is overclockign 'angle' but its still worth a read if you have time)- 

[http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html)
 
Short version for the lazy- with a 5870 video card (uses a fair bit of power by itself, up to 170watts) the absolute maximum they could drag out of a standard clocked Athlon II X635 was 316watts. That was an extrapolated figure, the most they could get the same CPU at stock speeds in  a 'real world' test was 250watts, and even that was pretty unrealistic (a high CPU use program running at the same time as a heavy GPU use program) 

> **el_Paraguayo said:**
> Software
 
Mythbuntu won't shutdown the PC - it seems to stop services, unmount drives etc. but won't power down. Is there any way to debug why it's not - e.g. particular logfile?
 
Thanks.

There probably is some way to debug, but I dont know offhand. You could always try shutting down from command line- 

Ctrl + Alt +F1 (drops you back to command line only)

sudo shutdown -h now

---

### Post by el_Paraguayo on 2011-02-16
Thanks (again) for the detailed answer.
 
The PSU is around 7 years old (but was never really abused by my old system - always silent and cold). The expanation about the various rails makes sense.
 
I'll look into a new supply.
 
The shutdown thing is weird as the machine reboots happily enough, just won't power down. I've been reading through posts on the site which talk about it being a wireless issue (I don't have a wireless device), something to do with OpenOffice (not installed) or ACPI settings. I do hope it's not the latter as I'd be interested in getting suspend/resume working on an alarm so the machine wakes up for scheduled recording.
 
I'll let you know how I get on.

---

### Post by cascade9 on 2011-02-17
> **el_Paraguayo said:**
> Thanks (again) for the detailed answer.
 
The PSU is around 7 years old (but was never really abused by my old system - always silent and cold). The expanation about the various rails makes sense.
 
I'll look into a new supply.
 
No problem. ;) 

BTW, you were lucky. I tried running a similar desktop system (Gigabyte 770T-USB3, Phenom II X2 550, 4GB DDR3, 8400GS and 1TB WD) on a thermaltake 430watt power supply,which was farily old but had less than a  years very light use. I got......segfault after segfault. Changed to a newer PSU (corsair HX520) and its super-stable.  

> **el_Paraguayo said:**
> The shutdown thing is weird as the machine reboots happily enough, just won't power down. I've been reading through posts on the site which talk about it being a wireless issue (I don't have a wireless device), something to do with OpenOffice (not installed) or ACPI settings. I do hope it's not the latter as I'd be interested in getting suspend/resume working on an alarm so the machine wakes up for scheduled recording.
 
I'll let you know how I get on.

It is weird. :S 

Hopefully suspend works, even if shutdown doesnt. Stanger things have happened. But it would be good to fix the shutdown problem.

---

### Post by el_Paraguayo on 2011-02-22
I bought a new power supply - this [Zalman ZM400-ST]("http://www.quietpc.com/gb-en-gbp/products/psus-400-500/zmx00-st").
 
I put this in the machine, switched it on... and was deafened by the noise coming from the machine!
 
The case fan was roaring - if the case was on wheels it would have been moving around the living room.
 
So, I figure the fan's getting more power from that supply than the old one. So I've unplugged that fan for the moment.
 
With the CPU fan and PSU fan the machine is still running nice and cold (lm-sensors shows 25 degrees - although I can't quite tell which temperature that's referring to).
 
I'll look at getting another case fan just in case though.
 
 
It didn't fix the shutdown problem though - I've started a [separate thread]("http://ubuntuforums.org/showthread.php?t=1692877") on that.

---

