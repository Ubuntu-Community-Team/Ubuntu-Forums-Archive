---
title: "Need help buying wireless PC card"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by numberexhaust on 2005-08-15
OK guys... I've given up on my Proxim Orinoco card... it has screwed me for the last time.  I know for a fact that the Lucent Wavelan card works on my system (I tried a friend's), but I can't find that online for a good price.

What is a good card I can buy (either online or at BestBuy, etc) that will be compatible with the drivers that come built into the kernel?  I'm looking at various D-Links, etc.

---

### Post by YorYor on 2005-08-16
[QUOTE=numberexhaust]OK guys... I've given up on my Proxim Orinoco card... it has screwed me for the last time.  I know for a fact that the Lucent Wavelan card works on my system (I tried a friend's), but I can't find that online for a good price.

What is a good card I can buy (either online or at BestBuy, etc) that will be compatible with the drivers that come built into the kernel?  I'm looking at various D-Links, etc.[/QUOTE]
 I've had a Linksys before, and except for a few minor difficulties, worked ok after the initial configuration was settled.
I now have a NetGear WG511 PCMCIA, which works as easy as it gets:
1. Plug it in
2. ndiswrapper
3. dhclient

I definitely would recommend the NetGear over the Linksys. I wouldn't know the range capabilities though... never did actually bother to test how strong it is.

Good luck!

---

### Post by numberexhaust on 2005-08-16
You know, I've had problems with ndiswrapper before... I don't really want to risk it again.  It would be preferred if the support for the card could be built into the kernel.

---

### Post by numberexhaust on 2005-08-16
[QUOTE=YorYor]I've had a Linksys before, and except for a few minor difficulties, worked ok after the initial configuration was settled.
I now have a NetGear WG511 PCMCIA, which works as easy as it gets:
1. Plug it in
2. ndiswrapper
3. dhclient

I definitely would recommend the NetGear over the Linksys. I wouldn't know the range capabilities though... never did actually bother to test how strong it is.

Good luck![/QUOTE]
 How do I use ndiswrapper with that particular driver?  I can only find a windows executable for it on their downloads site.

---

### Post by professor_chaos on 2005-08-17
NetGear WG511 PCMCIA worked for me on a HP laptop without any other software installs.

---

### Post by numberexhaust on 2005-08-17
Sweet... I actually just bought a WG511T and it works with ndiswrapper.  Let's see how well it holds out.

---

### Post by YorYor on 2005-08-18
[QUOTE=numberexhaust]Sweet... I actually just bought a WG511T and it works with ndiswrapper.  Let's see how well it holds out.[/QUOTE]
 Nice to hear that. :)
You actually need to extract that stupid NetGear executable file (which I think you already realised) before you can get at the main driver files... have half a mind to shoot them an email and tell them to be more Linux-friendly by offering alternate package types.

I just realised you wanted a card which worked with built-in drivers... my apologies for recommending one that still needed ndiswrapper.

No matter what, what's important is it works, so have fun!

---

### Post by numberexhaust on 2005-08-18
Yeah absolutely.... I was just afraid that I would go out and spend a lot of money and then realize it didn't work (because I had some pretty wierd troubled before), but I went to Best Buy and they had a 30 day return policy even after it was open, so I decided to go for it.  It goes much faster than my old card, so I think it was worth it.  Thanks again guys.

---

### Post by npaladin2000 on 2005-08-18
Get a D-Link card and the madwifi drivers (there's an RPM package floating around that can be installed with Alien)

---

### Post by numberexhaust on 2005-08-18
Well I already have a netgear wg511t, but would that work better with madwifi??

---

### Post by YorYor on 2005-08-20
[QUOTE=numberexhaust]Well I already have a netgear wg511t, but would that work better with madwifi??[/QUOTE]
 Don't think there's a need for it to "work better"... as long as it works at its rated specifications, and whenever and wherever you want it to right? :)

---

### Post by numberexhaust on 2005-08-20
[QUOTE=YorYor]Don't think there's a need for it to "work better"... as long as it works at its rated specifications, and whenever and wherever you want it to right? :)[/QUOTE]
 It works fine except sometimes DHCP will take a long time to connect (30 seconds to 1 min).  I know there are a couple of threads on this.

---

### Post by npaladin2000 on 2005-08-20
it'll work just fine.  Fact is, any Aethros card that won't work right with madwifi will work with ndiswrapper.  And with ndiswrapper you get the turbo modes. ;)

madwifi doesn't like my IBM miniPCI much (I think IBM did something screwey to it) but the ndiswrapper works fine and gives me 108 speed (matches up with my DLink a/g AP).  I just have to make sure the madwifi drivers don't load instead (Easy enough to remove the restricted modules from the 386 and 686 kernels, but I custom-compiled one for my pentm kernel...have to yank it out and re-compile I guess...needs more tweaking anyway). 

The other well-supported wireless chip in Linux is the Intel series, the ipw2100(b),2200(g), and 2915(a/g) chips.   Thing is, I'm not sure who makes PC Cards based on these chips...they're just found a lot in laptops in MiniPCI form. And NewEgg carries the Intel MiniPCI cards.

---

