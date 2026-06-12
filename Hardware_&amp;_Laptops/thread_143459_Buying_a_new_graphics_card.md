---
title: "Buying a new graphics card"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by ubuntukid on 2006-03-12
Seeing as I`m having so much problems with my Voodoo 3 card I decided to buy a new graphics card. I`m currently looking at the Club-3D GeForce MX4000 card. It`s got an agreable price tag and I`m just wondering if it will be compatible with ubuntu.

Take a look:
[http://www.ciao.co.uk/Club_3D_GeForce_MX4000__6272516](http://www.ciao.co.uk/Club_3D_GeForce_MX4000__6272516)

I`m not going to be playing demanding games or anything like that. I just need a card that works with ubuntu which will let me play tux racing when I feel like it and which doesn`t give me a slugish menu system like voodoo 3 does. The most demanding I`ll be playing is Quake 3 and it should be more than enough for that but will it be difficoult to set up and use on ubuntu?

---

### Post by ubuntukid on 2006-03-12
I just checked the amazon page and it says that it`s compatible.
[http://www.amazon.co.uk/exec/obidos/ASIN/B0001HWLAO/202-6446087-0628644](http://www.amazon.co.uk/exec/obidos/ASIN/B0001HWLAO/202-6446087-0628644)

---

### Post by Teroedni on 2006-03-12
[http://en.wikipedia.org/wiki/GeForce_4](http://en.wikipedia.org/wiki/GeForce_4)
a litle info about the card
Its a good card for the money ,with stable linux supports:)
It also supports the new eyecandy xgl and compiz

Go ahead and buy it;)

---

### Post by codejunkie on 2006-03-12
actually it is a very good card for the money, but as of right now it doesn't fully support Xgl it is unable to do smooth video playback because it lacks pixel shader support, so if your wanting eyecandy with Xgl. get a GeForce 5200 you can probably find one for around $50 US and it's well worth the money.

---

### Post by ubuntukid on 2006-03-12
Is this the card you mean?
[http://www.linuxbutikken.no/PartDetail.php?q=p:499126;c:36132](http://www.linuxbutikken.no/PartDetail.php?q=p:499126;c:36132)

Looks good. I`ll buy it if you can confirm that it should work with ubuntu. I won`t hold your head to ransom if it doesn`t :)

---

### Post by Lord Illidan on 2006-03-12
The Geforce FX 5200 might be what you need. Or else try the FX 5700.

---

### Post by ubuntukid on 2006-03-12
I keep seeing the GF 5200 under different branding names. Club 3D, WinFast Nvida, etc. Is it the same card under different names? Will they all work on Linux?

---

### Post by Lord Illidan on 2006-03-12
[quote=ubuntukid]I keep seeing the GF 5200 under different branding names. Club 3D, WinFast Nvida, etc. Is it the same card under different names? Will they all work on Linux?[/quote]

Yep. As long as it specifies that it is FX 5200. It is basically the chipset, GPU, with some manufacturer added features.
And yes, it should work on linux. Mine did.

---

### Post by codejunkie on 2006-03-12
[QUOTE=ubuntukid]I keep seeing the GF 5200 under different branding names. Club 3D, WinFast Nvida, etc. Is it the same card under different names? Will they all work on Linux?[/QUOTE]
nvidia just licences there gpu to different card manufactures, but they are nvidia graphics cards. and usually nvidia cards work great under linux.

---

### Post by Lord Illidan on 2006-03-12
Just avoid ATI. Nothing personal, understand, but nearly all the problems with graphic cards reported on Linux forums have to do with ATI graphics cards.

---

### Post by ubuntukid on 2006-03-12
Well, it looks like it`s going to be the FX 5200 for me then. Only one important question first. It says it uses AGP for connecting. How do I know if I have such a thing? I checked the Device Manager and it says that my current Voodoo 3 card is connected to an AGP bridge but when I select my Voodoo 3 card in the list it says Buss Type PCI. Do I have what I need to install the card?

---

### Post by codejunkie on 2006-03-12
[QUOTE=ubuntukid]Well, it looks like it`s going to be the FX 5200 for me then. Only one important question first. It says it uses AGP for connecting. How do I know if I have such a thing? I checked the Device Manager and it says that my current Voodoo 3 card is connected to an AGP bridge but when I select my Voodoo 3 card in the list it says Buss Type PCI. Do I have what I need to install the card?[/QUOTE]
if your motherboard has a slot like the brown one with the white clip, like in the attached picture 
[http://www.slo-tech.com/testi/plate01/agp_slot.jpg](http://www.slo-tech.com/testi/plate01/agp_slot.jpg)
you should be ok, if not it won't work. also if your not sure, google your motherboard model number, or go to the manufactures website, and find the specs for your motherboard. it should list all the avaliable slots pci, agp, pciexpress etc, as long as your motherboard has at least a 4x agp slot you'll be ok.

---

### Post by ubuntukid on 2006-03-13
I'm having problems finding out what kind of an AGP port I have. My computer is a Dell Dimension XPS T500. According to this site [http://www.betabreakers.com/tech_desktops.html](http://www.betabreakers.com/tech_desktops.html) it uses an Intel 440BX Mother Board chipset and an Intel Seattle (DELL) Motherboard Mfr and Model.

Can I use the graphics card? I don't mind not getting the most out of it just as long as it works.

---

### Post by codejunkie on 2006-03-13
[QUOTE=ubuntukid]I'm having problems finding out what kind of an AGP port I have. My computer is a Dell Dimension XPS T500. According to this site [http://www.betabreakers.com/tech_desktops.html](http://www.betabreakers.com/tech_desktops.html) it uses an Intel 440BX Mother Board chipset and an Intel Seattle (DELL) Motherboard Mfr and Model.

Can I use the graphics card? I don't mind not getting the most out of it just as long as it works.[/QUOTE]
i googled the specs you gave, and from what little i found on Google, 
it looks like it does have a 4x agp slot, so the new nvidia card should work, not at full speed but it will work. 
but before you buy the new card, pull the side of your case off, look at your motherboard and double check that it does have a slot that looks like the brown one in the picture i posted, if it does you should be just fine.

---

### Post by ubuntukid on 2006-03-13
I have taken it apart and checked inside and I do have an AGP slot. It even says AGP next to it. Problem was it didn't say if it was 2x or 4x etc. But I do have an AGP slot. My old Voodoo 3 card is currently connected to it but I'll be removing it as soon as I get the new one.

---

### Post by codejunkie on 2006-03-13
[QUOTE=ubuntukid]I have taken it apart and checked inside and I do have an AGP slot. It even says AGP next to it. Problem was it didn't say if it was 2x or 4x etc. But I do have an AGP slot. My old Voodoo 3 card is currently connected to it but I'll be removing it as soon as I get the new one.[/QUOTE]
from the specs i found on Google with the info you gave me, it is a 4x agp slot most new cards are 8x, and they will work just fine, but not at full speed in a 4x agp slot. my motherboard only has a 4x agp slot and it's working just fine with an Nvidia 6200 I'm just not getting the full potential of my video card.

---

### Post by ubuntukid on 2006-03-13
That's not going to be a problem. The plan is that once I've moved to england this summer I'll build my own computer but I'm buying some of the parts already now so that I can use them in my old computer while I wait. Things like graphics card, harddrives and DVD bruner. I can't afford to buy it all at once so I buy one part at a time and it makes sense to start by buying those parts that I can already use in my old computer.

---

### Post by codejunkie on 2006-03-13
[QUOTE=ubuntukid]That's not going to be a problem. The plan is that once I've moved to england this summer I'll build my own computer but I'm buying some of the parts already now so that I can use them in my old computer while I wait. Things like graphics card, harddrives and DVD bruner. I can't afford to buy it all at once so I buy one part at a time and it makes sense to start by buying those parts that I can already use in my old computer.[/QUOTE]
that's what I've been doing for years, it makes great sense if your on a budget.

---

### Post by ubuntukid on 2006-03-13
and the fact that I use ubuntu now as my os I don't have to pay load and loads of money for windows and all that. I stopped using windows completely about a month ago and I still don't regrett it so I have no plans of purchasing it when I build a new computer.

---

### Post by ubuntukid on 2006-03-13
Well I`ve purchased it now. Should arrive in 3 - 5 days.

Just one question though. How do I activate it once I`ve inserted it into my computer? Do I just put it inn, install the drivers with automatix and that`s it or is there more to it than that?

---

### Post by Teroedni on 2006-03-13
[QUOTE=ubuntukid]Well I`ve purchased it now. Should arrive in 3 - 5 days.

Just one question though. How do I activate it once I`ve inserted it into my computer? Do I just put it inn, install the drivers with automatix and that`s it or is there more to it than that?[/QUOTE]


Yea thats it:)

but you may have to change the driver parameters in your xorg.conf for ubuntu to be able to load xserver

Section "Device"
	Identifier	"xxxxx"
	Driver		"nv"
	BusID		"xxxx"
EndSection 

Setting the driver to nv will make sure you get into Ubuntu grapical:)

After that you install the graphics driver and use driver "nvidia"

---

### Post by Lord Illidan on 2006-03-13
I would edit the xorg.conf file under ubuntu and set the Driver to "vesa" first.

Then basically, yes, just put it in, and use automatix for the drivers.

---

### Post by ubuntukid on 2006-03-13
After I installed ubuntu for the first time a few weeks ago I did ALOT of messing around, did some things I should have done and a few things I probably shouldn`t have done. For one thing I installed ubuntu on my smallest harddrive which I shouldn`t have done. I have therefore decided to just reinstall the whole thing now that I know how it all works properly. Will the graphics card get identified correctly if I put it inn before doing this?

---

### Post by Teroedni on 2006-03-13
Yes it will be installed with the opensource driver nv . 




Then you can install the nvidia drivers afterwards which gives you 3d acceleration:)

---

### Post by bobpur on 2006-03-13
I see no one has answered this so I'll take a stab at it.
If you're talking about Ubuntu v5.10 (Breezy), Just put the CD into the drive and aside from answering a few questions about Language and Where to install, it's pretty straightforward.
You'll be prompted to update once the install is finished. Again, just a matter of clicking and answering.
 As soon as I installed everything and before the update; I opened up the repositories and let everything update. It helps with installing programs later.
  I don't know if doing this is necessary or correct but its worked for me so far.

---

### Post by ubuntukid on 2006-03-14
I see that the next version of ubuntu is not far away so I'll wait untill then before I do a clean install. Also it could be valuble learning experience to configure the card.

Also what is xserver? Is it something to do with games?

---

### Post by dermotti on 2006-03-14
Its what gives linux graphics.

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by imranj on 2006-03-14
If you are not constrained by budget try for the fx 6 series of cards, or go for Gf 4800 Ti , cool card, will give you full GPU power at a good price.

take care

---

