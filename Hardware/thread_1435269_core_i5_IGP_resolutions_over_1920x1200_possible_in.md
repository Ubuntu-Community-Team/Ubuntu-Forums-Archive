---
title: "core i5 IGP: resolutions over 1920x1200 possible? interface used?"
date: 2010-03-21
forum: Hardware
---

### Post by antiplex on 2010-03-21
dear community,

i currently plan the upgrade of my existing hardware and i therefore think about putting a system together based on intels new clarkdale core i5 600 series which comes with a integrated gpu meaning that it sits right in the cpu. 
i want a system with a low idle-power consumption and nice performance. some occasional gaming would be nice but havent found the time to play any 3d games in the last 24 months and i'm not sure when this will change.

the dell u2711 (27" 16:9 2560x1440) monitor seems like a nice thing along with my new machine but i wonder if resolutions over 1920x1200 (e.g. 2560x1440 or 2560x1600) are possible with ubuntu and the i5's igp.

i remember having heard that the igp of the core i5 can't handle dual-link dvi which would be necessary (since single link dvi's maximum is 1920x1200) and there seems to be only gigabyte offering a mainboard with a core i5 igp capable chipset with a display-port.

so i wonder if anybody has any experiences with running ubuntu at a resolution higher than 1920x1200 on a intel core i5 system using its integrated graphics.

what i have found out that support for the latest intel igp chipsets have been added since around 9.10 but there were plenty of bugs in the drivers leading to system chrashes or freezes.
situation seems to get better with the 10.04 betas, can anybody verify this?
there is an [interesting article on phoronix]("http://www.phoronix.com/scan.php?page=article&item=intel_clarkdale_gpu") about the new clarkdales and they mention the use of the upcomig 2.6.33 kernel which still didn't seem to solve the opengl-problems that ocurred, but i could not find out if this has been solved or if lucid's (10.04) 2.6.32 kernel should generally just work.

infos, comments and feedback welcome ;)

---

### Post by cascade9 on 2010-03-21
I wouldnt think that the intergrated 'GPU' on the i5s is going to anywhere near as good as a real GPU....intel tradionally has awful graphics. 

If your really after a low power system, then an Atom might work, but they are low power in various ways LOL. 

Another choice could be the 45watt TDP AMD chips- Athlon X2 235e and 240e, X3 400e and 405e, and X4 600e and 605e. Not quite as low power as the Atom, but a fair bit lower than the i5. Combined with a nVidia or ATI intergrated graphics chipset then you would actually get better graphics capabilites. But still limited to 1920 x 1200, as far as I know yuo will need an addon card to run a higher resolution than that (I'm not sure what you need with the newer nVidia cards, but with the 8xxx series 'select' 8400GSs can do dual-link)

---

### Post by antiplex on 2010-03-21
thanks for your comments, cascade9! i am fully aware of the fact that igp solutions go nowhere near a full graphics card.
i currently run a mainboard with a nvidia 630a onboard chipset (geforce 7050) which had enough power for what i needed (but can't do dual-link dvi).

i believe the core i5 igp should deliver better performance that the geforce 7050 (somewhere i read i5 gfx-performance is comparable to an amd hd 2600pro) plus i hope a resolution of 2560x1440 will be possible under ubuntu.

i was sticking with amd for years and always preferred lower idle-power and cheaper prices over a better full load performance with higher costs and power consumption of intel systems but as it occurs to me things have changed and besides the higher entry-price the current intel-cpus with integrated gpus beat amd by power consumption and performance.

---

### Post by cascade9 on 2010-03-22
I've heard claims for intel onbaord graphics before, and they have never delievered yet LOL but who knows? Maybe it will ahve similar levels of perfroamnce to the ATI 2600 HD (for display, anyway, considign its not even going to have DX10 I doubt it would come close for gaming). Debatable on the power consumption/performance, but unless you want to get into that, I dont feel the need (I pride myself on being a _borderline_ AMD fanboi, not one of the crazies). 

I've got some goodish and badish news for you- 

> HTPC fans will be pleased to see that Bitstream support is included, intimating lossless Dolby TrueHD and DTS HD Master Audio transported over HDMI (v1.3a). Connectivity-wise, you'll see boards outfitted with HDMI, DVI, VGA, and DisplayPort, and you'll need the latter if driving a 2,560x1,600 monitor; the HD Graphics don't support dual-link DVI.

[http://www.hexus.net/content/item.php?item=21683&page=7](http://www.hexus.net/content/item.php?item=21683&page=7)

---

### Post by antiplex on 2010-03-22
good point, intel igps for sure have so far been rather disappointing when it came to performance. i doubt the new hd-series will break with that tradition. but maybe ...
 
but what igp-alternatives are there on the market? havent heard anything convincing from nvidia and amd's 890GX is more or less just an overclocked 790GX which for sure is a considerable chipset but nothing ground-breaking as well. 
keep in mind my focus in this thread was on the chance of being able to deliver resolutions over 1920x1200 over a digital connection with a igp solution which seems hard to find since most available boards feature no display-port nor dual-link dvi capability.

so there seems to be not too much of a choice for now. :(

one notable point of intels h55/h57 platform (the one needed to use clarkdales igp) is that it should support dual digital output, so if i didn't get this wrong, it means that two displays can be attached via a digital interface (e.g. display port + hdmi).

this is the technical side, there is furthermore to consider what ubuntu/linux is capable of doing with all that... 
anybody tried something in this direction already?

---

### Post by Yellow Pasque on 2010-03-22
The hardware is not limited to single-link DVI:
> The IGP's display pipelines and video processing unit have both been substantially upgraded, as well, with near-best-in-class capabilities. The hardware supports dual displays, each at resolutions up to 2560x1600, and it can now drive two displays simultaneously over HDMI, which the GMA 4500 series couldn't do. Richer colors are on the menu thanks to support for 12-bit-per-channel Deep Color over DisplayPort and HDMI, along with xvYCC capability for an expanded color gamut with wide-gamut displays.-- [http://www.techreport.com/articles.x/18216/2](http://www.techreport.com/articles.x/18216/2)

Whether mesa (open-source 3D stack) can do direct rendering when the display is > 2048 in either direction is something I'm not sure of (it used to be an issue).

You could try to build your system and just use the IGP. The worst thing that could happen if the IGP isn't powerful enough is that you have to spend $50 or so (or the euro equivalent) and get a low-power video card (nvidia GT220 or RadeonHD4350).

---

