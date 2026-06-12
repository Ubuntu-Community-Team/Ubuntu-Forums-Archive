---
title: "nvidia card to replace integrated sis"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by h4mx0r on 2008-01-14
I got this SS31T xpc by shuttle and it came with integrated sis graphics controller. So far no working direct rendering for that device is available and out of the box I can't get more than 800x600 resolution. I was planning on getting a nvidia card like some other posters commented. The nvidia card would have to be pci express, although there is a 32 Bit PCI (v2.2) slot but that's slower than a pci express x16. 

The problem is my current power supply is limited and I don't want to replace yet another piece of hardware so guess no awesome 8000 series card. I heard from one forum post that the 7950 gt is pretty good but was unsure of such evidence. Oh also opengl support is a must I don't ever dual boot just sometimes use wine. I heard from opengl wiki that current cards support up to 2.1 opengl and 3.0 is still in the works.

PSU:
250 Watt PS3 Switching Power Supply with on/off switch and 9cm cooling fan
Voltage switch for 115/230V AC input voltage

no plans for anything besides hard drive, ram, fans, occasional usage of my flash drive keychain so that might save some power.

Someone posted on this other forum about using a separate power supply for the graphics card but that seems a bit unneccesary.
[http://www.hardforum.com/showthread.php?t=1114098](http://www.hardforum.com/showthread.php?t=1114098)

---

### Post by mikecool on 2008-01-14
The Geforce 8x serials(except 88) do not consume more power than 79xx, if my understanding is correct.

[http://en.wikipedia.org/wiki/GeForce_8](http://en.wikipedia.org/wiki/GeForce_8)
[http://en.wikipedia.org/wiki/GeForce_7_Series](http://en.wikipedia.org/wiki/GeForce_7_Series)

---

### Post by h4mx0r on 2008-01-14
Ah thanks didn't know there were individual wikis for each series. I was browsing some reviews over at newegg and somewhere it was mentioned max bandwidth I can get using the pci-e is 4.0gb/s but I couldn't quite understand what it meant it might be 5.4gb/s. I remember looking up the fx5200 in my desktop pc on nvidia site seeing a large chart with max bandwidth and other specs of all cards. Does anyone know where that link might be?

---

### Post by h4mx0r on 2008-01-15
After reading a good review of someone using the nvidia 7300gs with similar model I think I might go with that card. The high vertices/sec of the gs model would yield good trilinear filtering right? 6.5gb/s is slightly more bandwidth than is needed just to be on safe side. No clue what ramdac means but 400mhz sounds about right judging by what I read in the bios settings. The gt model of this card has a 128-bit memory interface is that a major difference?

nvidia site states:
geforce 7300gs
pci express
64-bit memory interface
6.5gb/s memory bandwidth
2.2 billion pixels/sec
413 million vertices/sec
400mhz RAMDAC

---

### Post by h4mx0r on 2008-01-18
Wow I can see why no one bothered to get linux drivers for this integrated video device. Tried it out under windows system and its rather pathetic, completely wastes cpu cycles every moment and I get next to no frames per second doing anything. I got an AGP v3.0 8x though might use that with nvidia 7950gt, which as discussed on ubuntu forums appears to be the best option for linux systems at the time and its spurring along the new sli techniques for quad cores so bound to be some pretty fancy features. 8x00 series seems to be mainly for directx10 fanboys and other overclocking fanatics experiments. Going to go rtfm again still don't understand this agp x8 vs pci-e x16 stuff.

---

