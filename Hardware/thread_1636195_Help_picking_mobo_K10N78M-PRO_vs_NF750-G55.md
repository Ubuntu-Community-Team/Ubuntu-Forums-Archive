---
title: "Help picking mobo K10N78M-PRO vs NF750-G55"
date: 2010-12-02
forum: Hardware
---

### Post by skippylou on 2010-12-02
I want to upgrade my 10 year old socket 478 motherboard.  The things I am looking for are:

1. painless linux compatibility;
2. At least one PATA interface;
3. Two PS2 ports;
4. Integrated Nvidia graphics compatible with CUDA (8100, 8200, 8300, 9300, 9400).

I have found two possibilities:

ASRock K10N78M-PRO intermittent freezing problem [http://ubuntuforums.org/search.php?searchid=77823830](http://ubuntuforums.org/search.php?searchid=77823830)

MSI NF750-G55  APIC problem [http://ubuntuforums.org/showpost.php?p=9548928&postcount=7](http://ubuntuforums.org/showpost.php?p=9548928&postcount=7)

Which satisy 2, 3 and 4.  Does anyone have any positive or negative experience with either of these boards regarding linux compatibility? 
Alternate suggestions are also welcome.  

Thanks, Skippy

---

### Post by cascade9 on 2010-12-03
Any patricular reason why you want onboard nvidia? 

A nice GT210/220 isnt expensive, wont use much power at all (about the same or a tiny bit more than oboard) and will have newer compute capability version (not that I think CUDA is much use at all except for a few rare instances). 

IMO nVidia chipsets have been going downhil for years now, and the AMD chipsets are generally much better. 

I've been running AMD 7XX and 8XX chipsets for ages, and never had a problem with them. You could have issues with some expansion chips (eg network) on some manufacturers AMD 7XX and 8XX chipset motherboards, but inngeneral they work very well. 

Its really easy to get a 770/870 chipset motherboard with PATA and 2 x PS2 ports.

*edit- AFAIK socket 478 only got released in august 2001. Not quite 10 years, but near enough ;)

---

### Post by skippylou on 2010-12-03
> **cascade9 said:**
> Any patricular reason why you want onboard nvidia? 

A nice GT210/220 isnt expensive, wont use much power at all (about the same or a tiny bit more than oboard) and will have newer compute capability version (not that I think CUDA is much use at all except for a few rare instances). 

IMO nVidia chipsets have been going downhil for years now, and the AMD chipsets are generally much better. 

I've been running AMD 7XX and 8XX chipsets for ages, and never had a problem with them. You could have issues with some expansion chips (eg network) on some manufacturers AMD 7XX and 8XX chipset motherboards, but inngeneral they work very well. 

Its really easy to get a 770/870 chipset motherboard with PATA and 2 x PS2 ports.

*edit- AFAIK socket 478 only got released in august 2001. Not quite 10 years, but near enough ;)

Thanks for the suggestion.  My previous experience was with some of their "monster" cards 9800GX2.  I only need minimal CUDA compatibility for some test programs.  I was not aware of these low end products like the GT210.

This certainly opens up my search.  I'll have to look at Intel platforms too.

As far as 10 years, I am sure that you are right.  The first five or six years of crashing versions of Windows seemed like an eternity.

Thanks again, Skippylou

---

### Post by howtieatie on 2010-12-03
well nice great

---

### Post by gradinaruvasile on 2010-12-03
I personally dont like neither MSI nor Asrock - these are the cheapest manufacturers and i had unpleasant experiences with both of them - more precisely their mobos failed in many cases.

I would personally recommend Asus (i heard Gigabyte is good too). I use almost exclusively Asus hardware for ~10 years (mobo/graphics) and had no hardware-related problems (Windows-specific issues dont count here as they are present in all brands).

Asus has the M4N78 series now with the nvidia chipsets (8200 or 8300). The middle class of tem (such as the -VM s) has only one ps2 port, but any mouse with USB is dirt cheap.
They have HDMI, digital and RGB output and 7.1 surround.
The lower class (-AM) has 2 PS2 ports, but not as many output ports - only one vga and 6 channel output.
Look around the asus site, it is well laid out, you can find any info easily.

I use a Asus M3N78-VM ( slightly older, but with bios upgrade can use even the 6 core phenom IIs), had absolutely no problems with it (nvidia MCP78S chipset).
The onboard nvidia graphics are great under Linux (perfect stability, VDPAU hardware decoding etc). I even play some games on it (Lord of the Rings online and such) and have no problems, the 8200 is surprisingly fast for an integrated video card.

Also i suspend the computer and it works perfectly well. I reboot only on kernel updates.

I use Debian Squeeze on it now, but it was working well with Ubuntu 9.04-9.10.

---

### Post by cascade9 on 2010-12-04
> **gradinaruvasile said:**
> I personally dont like neither MSI nor Asrock - these are the cheapest manufacturers and i had unpleasant experiences with both of them - more precisely their mobos failed in many cases.

I would personally recommend Asus (i heard Gigabyte is good too). I use almost exclusively Asus hardware for ~10 years (mobo/graphics) and had no hardware-related problems (Windows-specific issues dont count here as they are present in all brands).

LOL, I  recently replaced a MSI motherboard (AMD 770 chipset) that died with an asrock (nvidia chipset). The MSI was pretty bad, and after some of the other problems I've had with MSI I doubt I'll be touching one again...unless its MSI or asrock, then I might go MSI. The asrock motherbaord is the cheapest and nasitiest I've ever seen (and I owned a 'PC chips' motherboard in the 90s, so thats saying something). 

Asus is normally pretty good....not as good as they used to be IMO, but I could be biased. I've had several asus mobos die on me (av7 266-e, a7v 333, a7n 8x, a8n 5x). Gigabyte is what I' currently liking, they seem to actually be a lot better than they used to be (there used to be odd problems with gigabyte mobos and video cards). 

Thats just my opnion though, I'm not silly enough to think that the hardware I've seen is anywhere near a big enough data set to be conclusive. ;)

---

