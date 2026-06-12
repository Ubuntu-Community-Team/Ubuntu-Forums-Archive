---
title: "Laptop Ignores ISO"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by thenocturnalhoodie on 2009-01-10
Hey everyone,
So I just inherited an old laptop of my cousin's. It's a refurbished Dell XPS M140. From what google tells me, it's got:

Intel Pentium M 770 / 1.73 GHz  processor
533 MHz Data Bus
Mobile Intel 915GM Express Chipset
L2 cache 
2 MB  Cache size  
512 MB of RAM
DDR2 SDRAM - 400 MHz and over 
PC2-3200 
SO DIMM 200-pin  
80 GB - 5400 rpm HD
Windows XP Installed

That's what came up under the google search, at least. There's no documentation of the parts on the laptop itslef, and I have no manual, so it may be slightly off if it was refurbished and given new parts.

Anyways, 
I tried booting off the Ubuntu 8.04 LiveCD. I went to the boot menu, and selected to boot from CD/DVD/RW Drive. It gave a little loading screen for a sec, but then went straight to the Windows XP Loading and Log-On screen.

I want to make it completely linux, as I have no use for the Windows XP. So i'm not going to be mucking about with partitioning. All I'm wondering is why it is not recognizing my LiveCD.

Any ideas/help/tips?

---

### Post by taurus on 2009-01-10
How did you burn the CD?  Did you burn the ISO file as an image file or as a data file?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

---

### Post by oilchangeguy on 2009-01-10
also the 512mb of ram your stats list, may be the max. your computer could have less. it takes 384mb to even run the live cd.

---

### Post by thenocturnalhoodie on 2009-01-10
> **taurus said:**
> How did you burn the CD?  Did you burn the ISO file as an image file or as a data file?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

I don't really remember how I burnt it. I think it was an image file. However, I am not concerned that it's a problem with the CD. I have already used this same CD to load Ubuntu on the computer that I am currently using and typing on.

---

### Post by thenocturnalhoodie on 2009-01-10
> **oilchangeguy said:**
> also the 512mb of ram your stats list, may be the max. your computer could have less. it takes 384mb to even run the live cd.

I think it said that the standard was 512mb, so I'm thinking it's more likely that I have it. Because it also listed that the max ram was 2 GB, so I don't think that's the reason, either.

---

### Post by taurus on 2009-01-10
If the CD works (you would see a bunch of files and directories on it if you view it in windows), then it means the problem is with the BIOS.

---

### Post by thenocturnalhoodie on 2009-01-10
Is it possible that I need the password to my Cousins account on the windows? If I try to start it up in windows, it gives me the login. And of course, as fate would have it, I don't know her password. Would I need that to install Ubuntu?

---

### Post by oilchangeguy on 2009-01-10
> **thenocturnalhoodie said:**
> Is it possible that I need the password to my Cousins account on the windows? If I try to start it up in windows, it gives me the login. And of course, as fate would have it, I don't know her password. Would I need that to install Ubuntu?

no

---

