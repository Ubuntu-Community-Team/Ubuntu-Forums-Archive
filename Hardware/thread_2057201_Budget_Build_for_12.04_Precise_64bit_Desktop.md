---
title: "Budget Build for 12.04 Precise 64bit Desktop"
date: 2012-09-13
forum: Hardware
---

### Post by shreepads on 2012-09-13
Hi

Need to put together a 12.04 budget system which will primarily be used for browsing (including video streaming), Skype, managing photos, playing music/ videos (up to 1080p), LibreOffice and some light gaming (e.g. Solitaire, Hearts, Sudoku, World of Goo, FieldRunners, TuxCart, SuperTux, Gcompris, TuxPaint etc).

Will not be used for video/ audio editing, RAW image processing, 3D rendering or intensive gaming (e.g. FPS, Speed DReams etc).

OK to use a low resource desktop like XFCE if necessary, but would ideally like to use a more intensive one like Cinnamon or even Unity (I won't be using it!).

Starting point is the latest budget build(s) recommended by Anandtech on 
[http://www.anandtech.com/show/6182/fall-budget-system-buyers-guide](http://www.anandtech.com/show/6182/fall-budget-system-buyers-guide)

Not too keen on ITX so this build:

```
Intel Celeron G530 minitower system

Component Product                                    Price 
Case Fractal Design Core 1000                        $47 
Power supply Antec Earthwatts 380W                   $39 
CPU Intel Celeron G530                               $45 
Motherboard Biostar H61MGC                           $50 
RAM 1 x 4GB Corsair XMS3 DDR3-1333                   $20 
Solid state drive Intel 330 Series 60GB              $67 
Hard disk drive Western Digital 250GB WD2500AAKX     $60 
Optical drive Samsung SH-222BB/RSBS                  $19 
Operating system Windows 7 Home Premium 64-bit       $91 

  Cost with SSD: $378 
  Cost with HDD: $371 
```

Have some doubts about
- PSU: Antec Earthwatts not available where I live, what other sub 400W PSU would be good and not too expensive?
- CPU: Is the G530 HD Graphics capable of running Unity/ Cinnamon and 1080p video (in Linux) smoothly?
- Motherboard: Want to use Intel's own H61 as have found Intel mobos tend to work very well with Linux. Of course H61 doesn't have USB 3.0 so that's a drawback. And getting USB 3.0 support via PCIe cards in Linux seems like an iffy thing from reading around the interwebs. But do get PCIe 3.0 so that's nice...
- RAM: Is 1x4GB better or 2x2GB? Assuming will never need more than 4GB for the scenario outlined
- Storage: SSD out of question will probably go for WD Blue 500GB or so, should be sufficient for the needs?
- Optical drive: Probably go for a Asus one
- OS Win 7 for $91: Yeah, right!

Add-ons:
- Webcam: Any cheap good Linux compatible ones?
- Monitor: Preferably 20/ 21 inch, is there anything like a cheap good IPS panel monitor?

TIA for any suggestions!

---

### Post by Epodx64 on 2012-09-15
It'd personally stay away from the Celeron at all costs those things are junk and nothing but problems. If you wanted to go a little cheaper go with an AMD build not as nice as Intel but you'd be able to piece together something pretty decent on newegg.

---

### Post by whatthefunk on 2012-09-15
Another thing to make sure of is that the onboard graphics card will work with Linux.  On my Z68 mb, the on board graphics is not detected at all.

Agree about Celeron.  My old computer had a Celeron chip and it was garbage.

---

### Post by Epodx64 on 2012-09-15
If you're not looking to overclock you could get a G41 LGA 775 chipset w/ DDR3 Ram (Gigabyte GA-G41MT-S2PT) Get a nice quad core "core 2 quad" Q9450 should work nice get some crucial DDR3 ram. The GMA X4500 works fine under Ubuntu The Q9450 is a pretty damn good processor still w/ 8 GiB's or DDR3 Ram that should run anything you could possible throw at it and would be pretty cheap 50$ for the mobo 125ish$ for the processor 30$ for the Ram get a 500 watt psu too just to be safe.

---

### Post by varunendra on 2012-09-16
For the kind of requirements you mentioned, I'd recommend an AMD Sempron-145 with [Asus M5A78M-LE]("http://in.asus.com/Motherboards/AMD_AM3Plus/M5A78LM_LE/#specifications") (or even [LX]("http://in.asus.com/Motherboards/AMD_AM3Plus/M5A78LM_LX/#specifications") will do). If you are lucky enough, the 145 may get successfully unlocked to 2-cores, and can also be safely overclocked upto 3.2 GHz at stock voltage with even the cheapest type psu (I have run it successfully for 24hrs.+ @ 3.4GHz @ stock voltage with a cheap 250W i-Ball psu). Even if not, the combo will be better than the combination in your signature (have personally tested it against HP DX2480 with E7400 cpu).

Also, since you don't seem to need overclocking, why corsair? Get a 1333MHz 1x4 GB Kingston or Transcend RAM module. 2x2GB is definitely better, but only slightly and given your scenario, not worth the price difference IMHO. For PSU, go with any Cooler-Master sub400W model, or any decent one.

If you really care for USB3, then I'm afraid the budget will dramatically increase. For that addition, I'd recommend an AMD FX-4100 with [Asus M5A88-M]("http://in.asus.com/Motherboards/AMD_AM3Plus/M5A88M/#specifications"). The remaining specs may remain the same, but the overall power and features will rise (and so will the cost) equivalent to a decent 3d gaming rig.

Do tell us what you went with and how's the performance.

---

### Post by shreepads on 2012-09-17
Thanks for all the comments!

- This build is for someone else, not me. I'm going to continue using the build in my sign (just got a USB 3.0 expansion card working succesfully in it!) for the forseeable future...

- Re Celeron, I think Intel has made a mistake branding these low end Sandy Bridge chips (eg like the G530) with the 'Celeron' brand, given the poor impression the earlier range of Celeron chips created.
See this: [http://www.anandtech.com/show/5005/holiday-budget-system-buyers-guide/2](http://www.anandtech.com/show/5005/holiday-budget-system-buyers-guide/2)

- Re Z68, I think the chipset itself has no graphics capabilities, it uses the graphics in the Sandy Bridge cores (or a discrete card). Which CPU are you using on that Z68?

- Re LGA 775/ G41/ Q9450: Not too keen on a build using EOL components. And a quad-core seems over-kill for what I have in mind, not to mention more expensive.

- AMD, somehow have this impression that AMD parts are more power hungry and less Linux compatible (especially the onboard Radeon graphics), could be entirely wrong though, don't have any experience with them!

- Overclocking not really an option. I don't have much experience in it and given the thermal and power conditions where I live I don't want to try it. Yes, entry level memory modules (Corsair has a few of those as well) should do just fine..

---

### Post by whatthefunk on 2012-09-17
> **shreepads said:**
> - Re Z68, I think the chipset itself has no graphics capabilities, it uses the graphics in the Sandy Bridge cores (or a discrete card). Which CPU are you using on that Z68?

Core i5 3.1 GHz

---

### Post by shreepads on 2012-09-17
> **whatthefunk said:**
> Core i5 3.1 GHz

Hmmm probably Intel Core i5-2400 Sandy Bridge 3.1GHz (3.4GHz Turbo Boost) with Intel HD 2000 Graphics?

---

### Post by whatthefunk on 2012-09-17
Thats the one.

---

### Post by shreepads on 2012-09-18
> **whatthefunk said:**
> Thats the one.

Going a bit OT here, but have you seen this:
[https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

---

### Post by whatthefunk on 2012-09-18
> **shreepads said:**
> Going a bit OT here, but have you seen this:
[https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

I dont really care about it because I have a dedicated graphics card.  Never bothered to even try to get it working.  Thanks anyway though.

---

### Post by afulldeck on 2012-09-18
> **shreepads said:**
> Thanks for all the comments!

- AMD, somehow have this impression that AMD parts are more power hungry and less Linux compatible (especially the onboard Radeon graphics), could be entirely wrong though, don't have any experience with them!

I was under the same impression, however I read a couple of weeks ago that the newer bulldozer solves the power & corresponding heating issue. With the price of electricity these days I think this is an important issue. Anyone know for sure?

---

### Post by shreepads on 2012-09-21
> **afulldeck said:**
> I was under the same impression, however I read a couple of weeks ago that the newer bulldozer solves the power & corresponding heating issue. With the price of electricity these days I think this is an important issue. Anyone know for sure?

Do you mean Piledriver? Yes we should (although won't know for sure till the desktop CPUs are released later this year).

But even that is far behind Intel's old Sandy Bridge. Not to mention the even more power efficient Ivy Bridge which is currently expanding mass production.

See: [http://www.anandtech.com/show/5831/amd-trinity-review-a10-4600m-a-new-hope/8](http://www.anandtech.com/show/5831/amd-trinity-review-a10-4600m-a-new-hope/8)

At one level, for a desktop build power is not THAT important as it is for a laptop. For me the bigger concern is the (percieved) lesser Linux compatibility of integrated Radeon graphics, even with the open source drivers...

The integrated Intel graphics on my build have saved me far to many times to count, when the nouveau/ nvidia proprietary drivers developed problems after an update.

---

### Post by shreepads on 2012-09-26
OK some more research points...

Firstly, definitely not getting a discrete graphics card, partly due to price, but also space, power consumption and cooling inside a compact case.

Not considering EOL sockets/ chipsets, either Intel or AMD, may be cheap in the short term but power hungry and expensive/ impossible to upgrade in the future.

So for the CPU, it's basically Intel Sandy/ Ivy Bridge vs AMD APUs. 

Now the current lot of AMD A4/ A6/ A8 APUs and corresponding mobos are a dead end because they use FM1 sockets and the next generation APUs (Steamroller/ Piledriver) will use FM2 sockets, which AFAIK is not backwards compatible.

On the Intel side, instead of the Celeron, I think a better bet would be the Pentium Sandy Bridges, G620/630 which are a LITTLE more expensive than Celeron, but cheaper than the A6 APUs (where I live) and beat them pretty handily in Anandtech benches in all areas that are important for me:

[http://www.anandtech.com/bench/Product/406?vs=403](http://www.anandtech.com/bench/Product/406?vs=403)

Only issue would be whether the Intel HD graphics in G620/630 can keep up with Unity and light gaming demands...

Coming to mobos, just need to decide between H61 and B75. H61 is cheap and good but doesn't generally support Ivy Bridge and doesn't have USB 3.0.

B75 more expensive at present, but has all the goodies, faster memory, USB 3.0 and PCI slot. Only shortcomings (if you can call them that) are single SATA III port, single PCIe x16 port

---

### Post by shreepads on 2012-10-19
The new Trinity APUs seem interesting... A little low on x86 performance but probably 'good enough'. And integrated video performance much better than Intel anyway.

Price for the entry level A4-5300 is around $65, so roughly the same as the Pentium G620/630 and with 65W TDP so decent power consumption as well (especially at idle).

If you can spend $10 more you can get the unlocked A6-5400K which, apart from being unlocked, also has other benefits like better GPU and clock speeds. But overclocking will probably send the temps up considerably (if it's anything like the A8s and A10s).

Motherboards a little expensive right now, but should come down...

AMD has committed to support this FM2 socket for the next generation Steamroller as well, where there should be significant boost in x86 performance and graphics as well, so seems reasonably upgradeable.

Only thing missing is PCIe 3.0 and speeds above DDR3-1866, but that's not a big loss for a budget build...

Initial feedback (for the A4-5300) on NewEgg seems positive, including one poster claiming: 

> "Running Ubuntu on it with the catalyst 12.9 beta drivers and WoW runs at 40fps on fair settings at 1680x1050"

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819113283&name=Processors-Desktops](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113283&name=Processors-Desktops)

Hopefully should see more reviews of this vs the Pentiums on the usual tech sites, but maybe not. Those guys only seem to care about the latest and greatest CPUs, usually Win only.

---

