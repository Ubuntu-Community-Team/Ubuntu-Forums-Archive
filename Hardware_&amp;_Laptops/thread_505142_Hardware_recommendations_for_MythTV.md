---
title: "Hardware recommendations for MythTV"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by Joe Jarvis on 2007-07-19
There are a lot of forum posts about hardware support problems, but I thought I would write a report about a successful new MythTV box.

My goals were:
1. receive HDTV over the air
2. drive a 1080p60 monitor
3. low cost
4. minimizing the number of discrete hardware pieces (less hardware = less headache!)
5. support a RAID-5 array of cheap disks
6. digital optical out for my A/V receiver

...and the kicker:..

7. the hardware vendor either had to commission or actively support free & open source drivers so that I could install Ubuntu and have everything Just Work and get better with updates

The core of my system ended up being...

Intel DG965WHMKR motherboard (~$65 refurb @ mwave)
pcHDTV hd-5500 OTA HDTV tuner (~$90 on ebay used, ~$130 new)
Prolink PV-CH7315 HDMI out card (~$45 new)

Pick your favorite flavors of CPU, RAM, discs, etc.  A bit about my choices...

While they haven't released the specs, Intel is paying X.org guru Keith Packard & others to actively develop FOSS drivers for Intel's on-board GPUs. Coincidentally, Intel's new G965 northbridge can handle resolutions up to 1080p60.  Intel has a novel ADD2/SDVO card system for providing ports to the integrated GPU via the board's graphics slot.  While the Prolink card is the only piece i haven't installed yet, it's likely to have driver support for driving an HDTV, if not already.  The motherboard has integrated gig-e (open source Intel driver), optical digital out sound (open source Intel driver), and six SATA controllers for cheap disk arrays.  There's kernel support for the pcHDTV tuner and MythTV supports it well.  I installed Gutsy fresh, configured MythTV using its GUI, and everything Just Worked!  No driver wrangling needed and the bug fixes should come nice and clean through the updates.

My only caution is the motherboard only accepts 1.8V 800 MHz RAM (I learned about that fine print the hard way.)

---

