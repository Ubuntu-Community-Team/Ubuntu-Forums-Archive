---
title: "Small, cheap, &amp; capable dual-screen workstation &amp; media center; does it exist?"
date: 2015-02-25
forum: Hardware
---

### Post by tessk2 on 2015-02-25
I am looking for a small form-factor machine to replace my desktop. Right now I am considering the Intel NUC, or a refurbed T430 Lenovo ThinkPad, but they will both end up being ~$500 once they're fully spec'd out. I already have the monitors, I just need something to run Xubuntu 14.04. Any other ideas?

---

### Post by weatherman2 on 2015-02-25
Most new desktop towers (or small form factor cases) should have two video connectors to allow you to use two monitors.

The question is, what do you need as far as specs?  I've seen some Intel Atom ("Celeron") boxes pretty cheap - these are Bay Trail multi-core which won't be very fast but may still be adequate for basic use.  Finding one for well under $500 shouldn't be too hard.  If you find a motherboard with integrated CPU, you may be able to build your own for well under that, though it won't be as small as the Intel NUC.

---

### Post by tessk2 on 2015-02-25
Mostly just media playback, including HD movies & streaming (Netflix), web browsing, running an IDE to write some code and compile LaTeX documents.

---

### Post by mastablasta on 2015-02-26
> **tessk2 said:**
> Mostly just media playback, including HD movies & streaming (Netflix), web browsing, running an IDE to write some code and compile LaTeX documents.

have a look at AMD A4 and A6 combos. weaker than soem intels but goodr GPU and cheaper. i guess you get what you pay :-)

---

### Post by kerry_s on 2015-02-26
i been thinking about getting one of these for something like that:
[http://www.amazon.com/gp/product/B00R7R1GWK/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER](http://www.amazon.com/gp/product/B00R7R1GWK/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER)

been sitting in my amazon cart for awhile. ram sounds like it would be easy to upgrade, 32gb ssd is fine for me as i usually keep important things externally.
just not sure how linux friendly it is, been checking the reviews for any linux install reviews but none so far.

---

### Post by weatherman2 on 2015-02-26
Amazon would probably sell a few more of those if they fixed the incorrect CPU listed at the top of the page.  It says the CPU is an ancient Celeron T3000 (which is based on Core 2 Duo, predating the i3), but if you read carefully below in the specs, the CPU is really a 2957U, which is much newer.  Perhaps HP has several versions of this same design over the years or something and this is just the latest version.

I would note that if the wireless card is really only 1x1 (150Mbps) as listed near the correct CPU name, that might be a limiter, as HP limits upgrading of wireless cards in its laptops to only a few approved models, so they may also prohibit upgrading it in this design.  (a "2x2" wireless card can do 300Mbps upstream and downstream.)  You'd also have the option to use one of the USB ports for a faster wireless card, but obviously it would be nice not to waste one when you could have an internal card.

---

### Post by tessk2 on 2015-02-27
> **kerry_s said:**
> i been thinking about getting one of these for something like that:
[http://www.amazon.com/gp/product/B00R7R1GWK/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER](http://www.amazon.com/gp/product/B00R7R1GWK/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER)

been sitting in my amazon cart for awhile. ram sounds like it would be easy to upgrade, 32gb ssd is fine for me as i usually keep important things externally.
just not sure how linux friendly it is, been checking the reviews for any linux install reviews but none so far.


Hey thats a good idea. How would it compare, though, to the Celeron based NUC?

[http://www.amazon.com/Intel-DN2820FYKH-Celeron-N2820-support/dp/B00HVKLSVC/ref=sr_1_1?ie=UTF8&qid=1425066979&sr=8-1&keywords=intel+nuc+celeron](http://www.amazon.com/Intel-DN2820FYKH-Celeron-N2820-support/dp/B00HVKLSVC/ref=sr_1_1?ie=UTF8&qid=1425066979&sr=8-1&keywords=intel+nuc+celeron)

Also I'm not sure how the performance of that Celeron CPU would compare either to something closer to a full desktop replacement. 

I also found some nice vids on this guy's channel about installing Ubuntu 14.04 on the i5 NUC, along with some tentative performance overviews

[https://www.youtube.com/watch?v=2bz65IRgR4Y](https://www.youtube.com/watch?v=2bz65IRgR4Y)
[https://www.youtube.com/watch?v=2bz65IRgR4Y](https://www.youtube.com/watch?v=2bz65IRgR4Y)

Also, thanks to that HP Stream listing, I found out that there are other tiny PC's and PC kits that are similar to the NUC. Not sure how I missed these. Anyone have experience using them with Ubuntu 14.04? I am gonna have to look up more on these, though they all seem to fall in the same price ranges as the NUC.

[ASUS VivoPC-VM40B-02 Desktop]("http://www.amazon.com/Asus-VivoPC-VM40B-02-ASUS-Desktop/dp/B00KU54KPQ/ref=pd_cp_pc_0/176-3544151-4924665")
[ASUS VM60-G072R Desktop]("http://www.amazon.com/VM60-G072R-Desktop-i5-3337U-Processor-Windows/dp/B00J2FA7TS/ref=pd_sim_pc_4?ie=UTF8&refRID=1RT5SM6HKP2PYXM0HYJY")
[ASUS VM60-G106M Barebone System]("http://www.amazon.com/dp/B00LHYG44Y/ref=psdc_565098_t1_B00J2FA7TS")
[Gigabyte Mini Intel Core i7-3537U 2GHz Compact PC Barebone]("http://www.amazon.com/dp/B00DGGWR3I/ref=psdc_565098_t3_B00J2FA7TS")
[ASUS CHROMEBOX-M075U]("http://www.amazon.com/dp/B00JY4Q52U/ref=psdc_565098_t1_B00KU54KPQ")

With this many options, and assuming the performance on these devices are good enough to run full desktop OS's, it makes you wonder why casual PC users would still go for the giant tower-style PCs. I've got one right now and can't stand it. I never actually use the extra performance (FX-8320 + GTX 750ti + 12GB RAM), it takes up a lot of space and power, though it does make a good space heater in the cold winter.


> **mastablasta said:**
> have a look at AMD A4 and A6 combos. weaker  than soem intels but goodr GPU and cheaper. i guess you get what you pay  [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

That was actually the first thing I looked at but I could not find them in the tiny form-factors of the devices listed in here. Even standard mITX cases like the Cooler Master Elite 130 are still way bigger than I want.

---

### Post by weatherman2 on 2015-02-27
> **tessk2 said:**
> Hey thats a good idea. How would it compare, though, to the Celeron based NUC?

[http://www.amazon.com/Intel-DN2820FYKH-Celeron-N2820-support/dp/B00HVKLSVC/ref=sr_1_1?ie=UTF8&qid=1425066979&sr=8-1&keywords=intel+nuc+celeron](http://www.amazon.com/Intel-DN2820FYKH-Celeron-N2820-support/dp/B00HVKLSVC/ref=sr_1_1?ie=UTF8&qid=1425066979&sr=8-1&keywords=intel+nuc+celeron)



The HP linked above has a Celeron 2957U which, if you look it up, is really a low-cost version of Haswell (4th generation i3/i5/i7).

The Intel NUC has a Celeron N2820, which is an entirely different CPU architecture called "Bay Trail" which is a successor to the old Atom CPU used in netbooks. (Intel uses names like "Celeron" as marketing names now, mostly).    Bay Trail was designed for low power, to be used in netbooks, tablets, and phones.  It will use less power and generate less heat (think quieter fan, if any) than something like Haswell, but Haswell should give you superior performance.

If you search the web for the CPU benchmark of both CPUs, you see the 2957U (1.4GHZ) has a benchmark of 1514 while the N2820 (2.13GHZ) has a benchmark of only 1003.  That's not a perfect comparison; the CPU architectures are different.  I think those benchmark numbers are for single core only, and both are dual core.  But I'd expect the 2957U to be generally faster, though (say about 50% faster), including the integrated video performance.

Will the CPU performance really matter that much?  Not sure.  I'll bet even the Intel NUC will be able to stream HD video just fine but probably not while doing anything else.

The Intel NUC does have a better wireless card than the HP, and as I noted above you may limited choice (if any) to upgrade the HP's wireless card.

I'd look at things like how much RAM you can add to either one.  Haswell support more RAM (16GB) than Bay Trail (8GB), but the upgrade options may be limited by the board design anyway.  And you may not care that much for an application like this.

---

### Post by kerry_s on 2015-02-27
i moved away from nuc shopping cause someone gave a heads up on issues with bios(i think), can't remember, but i been shopping for anything other than nuc.
i like the hp cause the ram & drive is upgrade able, not really worried about wifi cause i have a usb wifi that's fully linux compatible(ralink).

1 of the reviews said he just added 8gb ram giving him 10gb of ram, that's pretty much my plan for upgrades. it's already setup to run 2 monitors which is the plan, i'm going for 2 matching 27" inch tv's i already have in the house.

my current setup is pieced together from several non working pc's, which is why i have been shopping around for something newer, these are all old parts & it's only a matter of time before i start to get breakage.

---

### Post by tessk2 on 2015-02-27
> **weatherman2 said:**
> The HP linked above has a Celeron 2957U which, if you look it up, is really a low-cost version of Haswell (4th generation i3/i5/i7).

The Intel NUC has a Celeron N2820, which is an entirely different CPU architecture called "Bay Trail" which is a successor to the old Atom CPU used in netbooks. (Intel uses names like "Celeron" as marketing names now, mostly).    Bay Trail was designed for low power, to be used in netbooks, tablets, and phones.  It will use less power and generate less heat (think quieter fan, if any) than something like Haswell, but Haswell should give you superior performance.

If you search the web for the CPU benchmark of both CPUs, you see the 2957U (1.4GHZ) has a benchmark of 1514 while the N2820 (2.13GHZ) has a benchmark of only 1003.  That's not a perfect comparison; the CPU architectures are different.  I think those benchmark numbers are for single core only, and both are dual core.  But I'd expect the 2957U to be generally faster, though (say about 50% faster), including the integrated video performance.

Will the CPU performance really matter that much?  Not sure.  I'll bet even the Intel NUC will be able to stream HD video just fine but probably not while doing anything else.

The Intel NUC does have a better wireless card than the HP, and as I noted above you may limited choice (if any) to upgrade the HP's wireless card.

I'd look at things like how much RAM you can add to either one.  Haswell support more RAM (16GB) than Bay Trail (8GB), but the upgrade options may be limited by the board design anyway.  And you may not care that much for an application like this.


Thanks for that explanation. I saw that the two Celerons were different generations but wasn't aware of the performance of the two. 

Getting stuck with only an 8GB limit doesn't sound too bad *now*, but it reminds me of the desktop I bought in 2009 that has a 4GB limit. Been regretting that one ever since. So maybe 16GB supported is the way to go. 

Personally, I am trying to get a full desktop replacement. I'm coming from an FX-8320, so I don't think I could go with less than an i3. I might end up saving for the i5 version. It would be nice to have a computer that I don't need to upgrade for a while. I also had in mind running a Windows 7 virtual machine; I wouldn't expect the Celeron to handle that well, maybe the i3 would be ok with it? The extra RAM would also probably help with that.

---

### Post by tessk2 on 2015-02-27
> **kerry_s said:**
> i moved away from nuc shopping cause someone gave a heads up on issues with bios(i think), can't remember, but i been shopping for anything other than nuc.
i like the hp cause the ram & drive is upgrade able, not really worried about wifi cause i have a usb wifi that's fully linux compatible(ralink).

1 of the reviews said he just added 8gb ram giving him 10gb of ram, that's pretty much my plan for upgrades. it's already setup to run 2 monitors which is the plan, i'm going for 2 matching 27" inch tv's i already have in the house.

Oh yeah I remember reading about the BIOS issue. It was mentioned in [this]("http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/") article ([here]("http://www.anandtech.com/show/7566/intels-haswell-nuc-d54250wyk-ucff-pc-review/5") is another I had read that didn't mention it). Both of those articles are old by now though, and in the video I listed a few posts back the guy was able to install Ubuntu 14.04 without a hitch. So maybe the BIOS issue has been fixed? I guess you would have to make sure you are getting the most up-to-date version of the NUC for this to work out of the box; I remember some versions have a '1' at the end of the model number, maybe this could be an indicator of a revision that fixed this issue?

Also, can you link to the USB wifi adapter that you are using? The ones I have don't work well with Ubuntu 14.04 and I gave up trying to get them working. 

For RAM I might end up cheaping out and getting a 4GB stick to get started, and then tossing in a 8GB stick down the line, for a final total of 12GB.

It might also be worth noting that I read somewhere about new models of the NUC coming out very soon, including an i7 version. I am hoping for some price cuts to the current line-up if that happens.

---

### Post by kerry_s on 2015-02-27
this is the wifi usb i got:
[http://www.amazon.com/gp/product/B00762YNMG/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00762YNMG/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

i'm not sure about ram either, i currently have 2gb & it's been more than enough ram, i watch tv & movies, netflix, youtube,... all day no problem. i probably won't even upgrade the ram unless i find it on sale, dirt cheap. lol

---

### Post by weatherman2 on 2015-02-27
> **tessk2 said:**
>  I also had in mind running a Windows 7 virtual machine; I wouldn't expect the Celeron to handle that well, maybe the i3 would be ok with it? The extra RAM would also probably help with that.

I'm running Ubuntu 12.04 on my Acer netbook with 16GB of RAM.  It has only a wimply Celeron Sandy Bridge (dual core), but it runs XP in a virtual machine surprisingly well.  I believe it has hardware support for the virtual machine built into the CPU, maybe that helps.  Having a lot of RAM probably helps, too. Remember, "Celeron" doesn't really mean "slow" anymore.  The main difference between a Celeron Haswell and an i3 Haswell is that both are dual core but the i3 is multi-threaded - a poor man's quad core (but not quite).

I could live with 8GB of RAM now, probably - I upgraded a few years ago when laptop RAM was pretty cheap.  It is nice to have more.  I wouldn't want to be stuck with 4GB - I have a laptop with 4GB that I use regularly and do notice the difference.

---

### Post by mastablasta on 2015-03-02
are you sure you mean Celeron and not Pentium? as i know Pentiums are washed down i3, not celerons. or at least that used to be the case.

---

### Post by weatherman2 on 2015-03-02
> **mastablasta said:**
> are you sure you mean Celeron and not Pentium? as i know Pentiums are washed down i3, not celerons. or at least that used to be the case.

I mean Celeron.  Intel uses "Pentium" for the same purpose now, though.  A "Pentium" should be a little faster than the "Celeron" of the same family of processors.  "Celeron" is at the bottom.

---

