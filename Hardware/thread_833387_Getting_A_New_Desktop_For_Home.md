---
title: "Getting A New Desktop For Home"
date: 2008-06-18
forum: Hardware
---

### Post by SupaRice on 2008-06-18
So I'm about to take the plung and buy a new PC for home.  Which I mostly use as a Samba server, DNS server, and Virtualization.  I also want to be able to edit some videos on it, nothing fancy just videos of the kid.

So what is the most Ubuntu friendly hardware?  NVIDIA for graphics?  I'm looking for a quad core box, and would like to do RAID.

Suggestions of what to look for, and or stay away from?

Thanks in advance!



*** I should probably add that I'm most likely going to get a bare bones kit, and just put it inside my existing case.  What's the best sort of video card these days?

---

### Post by housam on 2008-06-18
have a look at system 76 [[COLOR="Red"]_desktops_[/COLOR]]("http://system76.com/index.php?cPath=27") specs.

---

### Post by SupaRice on 2008-06-18
> **housam said:**
> have a look at system 76 [[COLOR="Red"]_desktops_[/COLOR]]("http://system76.com/index.php?cPath=27") specs.

Those look pretty nice, but are a bit high for what I'm looking to spend.  That's why I'm probably going to DIY on this one.  Just wondering in general terms what to avoid and what to look for.  Especially in regards to video.

---

### Post by PhilMcRevis on 2008-06-18
As far as video and virtualization goes I would think a quad core would be well suited for it.  In theory, a 64bit processor would be better than a 32bit processor because you would have twice the throughput per clock cycle.  Of course, you'd have to actually be running software compiled for 64bit before it actually makes use of that and your hard drive may become the bottleneck first.

Lots of ram would be a must for the video and the virtualization.  4gigs(32bit limit) is fairly cheap.

nvidia seems like it is still the way to go with graphics but from what I've seen ati is coming along (but starting way behind in linux support).

---

### Post by SupaRice on 2008-06-18
Is PCI-x the way to go on a video card?

---

### Post by logos34 on 2008-06-18
> **SupaRice said:**
> Is PCI-x the way to go on a video card?

that's the standard these days.  they can get expensive, though, depending on  how much ddr2/3 video ram you want and how fast, HDMI, chipset, etc.).  
> 
I should probably add that I'm most likely going to get a bare bones kit, and just put it inside my existing case.

the barebones kits are overpriced (and usually you just get the board and case!)--get the mobo, case and everything separately.  true DIY

---

### Post by SupaRice on 2008-06-19
> **logos34 said:**
> that's the standard these days.  they can get expensive, though, depending on  how much ddr2/3 video ram you want and how fast, HDMI, chipset, etc.).  


the barebones kits are overpriced (and usually you just get the board and case!)--get the mobo, case and everything separately.  true DIY

Yeah I've got a case, cables, power, SATA drives, etc.  I was just going to get a CPU / MOBO / Memory combo.  I've got everything else.  Just I was looking at the cost of mainstream PC and they are expensive!

---

### Post by logos34 on 2008-06-19
> **SupaRice said:**
> Yeah I've got a case, cables, power, SATA drives, etc.  I was just going to get a CPU / MOBO / Memory combo.  I've got everything else.  Just I was looking at the cost of mainstream PC and they are expensive!

ok, I see.  In that case head over to newegg.com--they might even have a combo sale (cpu+board).  They have intel quads and some new amd phenoms (x4 and x3). 

Make sure you're power supply is up to the task--quad core and vid cards suck a lot of juice.  When you add in multiple drives (raid)--jeez, I think you're looking at a 500W+ psu.  (Seasonic, OCZ, PC P &S, Antec NeoPower series, etc -- don't skimp).

Do a title search for raid in [the ubuntu docs]("https://help.ubuntu.com/community/") for setup tips.

good luck

---

### Post by SupaRice on 2008-06-19
I just bought a Dell Insperion 530 off their outlet site.  It was $460 for a quad core (Q6600) 2GB DDR2 800mhz, 500GB 7200 RPM SATA drive, yada yada.... I thought that was a good enough deal, and it comes with a warranty.

I'll probably add 2GB RAM to it and see how the 128mb Nvidia card goes for now.

---

### Post by logos34 on 2008-06-19
sounds good

---

### Post by natibo on 2008-06-20
I would not recommend a System76.  I purchased one months ago and have had many problems.  They always seemed to blame something I did, and I had to reinstall Ubuntu many times.  I finally convinced them it was a hardware problem.  Now I have to send it back to them for repair.  On top of that, becasue I don't have the original box, if it breaks during the shipping back to them I am responsable.

---

### Post by SupaRice on 2008-06-23
> **natibo said:**
> I would not recommend a System76.  I purchased one months ago and have had many problems.  They always seemed to blame something I did, and I had to reinstall Ubuntu many times.  I finally convinced them it was a hardware problem.  Now I have to send it back to them for repair.  On top of that, becasue I don't have the original box, if it breaks during the shipping back to them I am responsable.

I had similar problems with Alienware last year.  I bought the "baddest mofo" they had.  It ended up costing me $200 to send it back and not have them post to my credit report.  They said that I never sent them back one of the hard drives for the laptop during the many many troubleshooting sessions.  I had it for just about 2 months and it never worked a single day.  And I had to fight with them on the phone for weeks to take it back without charging me a "restocking fee".  Errrrgghh!

---

### Post by stchman on 2008-06-23
> **SupaRice said:**
> So I'm about to take the plung and buy a new PC for home.  Which I mostly use as a Samba server, DNS server, and Virtualization.  I also want to be able to edit some videos on it, nothing fancy just videos of the kid.

So what is the most Ubuntu friendly hardware?  NVIDIA for graphics?  I'm looking for a quad core box, and would like to do RAID.

Suggestions of what to look for, and or stay away from?

Thanks in advance!



*** I should probably add that I'm most likely going to get a bare bones kit, and just put it inside my existing case.  What's the best sort of video card these days?

If you have some computer assembly knowledge you can build one pretty inexpensive and get great performance.

I built a PC and it was 100% compatible with Ubuntu OOB.

Processor - Core 2 Quad Q6600 (OC'd to 3.0 GHz on stock cooler)
Mobo - Asus P5K
RAM - Mushkin 2G (2x1GB) DDR2
Video - Nvidia GeForce 8800GT
HDD - Seagate SATA 3G 750G
Optical - (2) Samsung 20X SATA DVD burners
Case - Cooler Master
PS - Thermaltake 500W

I used an Audigy 2 sound card , but you can use the onboard to save some $$$$$.

The chipset, ethernet, firewire, USB, everything worked with the Live CD.  All I had to do was enable the restricted nvidia driver.

I think I spent about $900 and it really screams.  I dual boot Vista for gaming and Ubuntu for everything else.

---

### Post by SupaRice on 2008-06-24
> **stchman said:**
> If you have some computer assembly knowledge you can build one pretty inexpensive and get great performance.

I built a PC and it was 100% compatible with Ubuntu OOB.

Processor - Core 2 Quad Q6600 (OC'd to 3.0 GHz on stock cooler)
Mobo - Asus P5K
RAM - Mushkin 2G (2x1GB) DDR2
Video - Nvidia GeForce 8800GT
HDD - Seagate SATA 3G 750G
Optical - (2) Samsung 20X SATA DVD burners
Case - Cooler Master
PS - Thermaltake 500W

I used an Audigy 2 sound card , but you can use the onboard to save some $$$$$.

The chipset, ethernet, firewire, USB, everything worked with the Live CD.  All I had to do was enable the restricted nvidia driver.

I think I spent about $900 and it really screams.  I dual boot Vista for gaming and Ubuntu for everything else.

Yeah, I just bought one off of Dell's refurb site with similar specs, and got a 24" widescreen monitor for just over $700.  That's why I just went ahead and bought it, much much eaiser.  I'm up and running on Ubuntu on it right now, and never had to even use a screwdriver!  That's a great new experience!  :lol:

---

### Post by brons2 on 2008-06-24
Where's the fun in that??

anyways...

Be careful to test your new Dell when you get it.  I'd run a memtest86 and Prime 95 on it, that will usually find any hardware problems.  My ex-wife worked support with Dell when they actually did it here in Texas and not in India.  A lot of the factory outlet "refurbished" systems would get repeat calls for the same issues that their original owners had.

---

### Post by tubbygweilo on 2008-06-24
Good luck with your venture, as it is summer in my part of the world I would suggest that you give a bit of thought to cooling your new system and perhaps a quick visit to [silentpcreview]("http://www.silentpcreview.com/") may be time well spent.

---

