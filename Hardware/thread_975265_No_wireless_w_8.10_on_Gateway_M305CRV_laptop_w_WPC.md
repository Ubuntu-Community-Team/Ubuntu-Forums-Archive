---
title: "No wireless w/ 8.10 on Gateway M305CRV laptop w/ WPC11 card"
date: 2008-11-08
forum: Hardware
---

### Post by Bailywolf on 2008-11-08
I got Ibex working on my Gateway M305CRV laptop last night- turns out doing a 4x burn on the install CD (and doing a second on with the ISO and the Wubi exe) took care of the errors I was having.

So I did the Ubuntu in Windows install to really kick the tires before I commit to a total rebuild, but...

I've got a v.3 Linksys WPC11 PCMCIA wireless card, which according to [this ]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys")should be supported out of the box, but no dice.  

Ubuntu finds the ethernet card just fine, but doesn't find the wireless card at all.  I checked to make sure it wasn't misidentifying the wireless card as ethernet, and it's not.  

Do I need some special drivers for the card here, or some to run the PCMCIA slot?

Thanks,

-B

---

### Post by sc0tt10 on 2008-11-08
If you already have the windows XP drivers, search for Ndiswrapper and the graphical frontend, it will enable you to get the XP drivers working with ubuntu as though it is officially supported.

---

### Post by Bailywolf on 2008-11-08
> **sc0tt10 said:**
> If you already have the windows XP drivers, search for Ndiswrapper and the graphical frontend, it will enable you to get the XP drivers working with ubuntu as though it is officially supported.

Hmmm... looking at this right now, and it seems like a deeper rabbit hole than I was hoping for.  

How tricky is this to set up?

-B

---

### Post by sc0tt10 on 2008-11-08
its only a five minute job, assuming you have access to a wired network on the laptop just search for ndisgtk and get the .deb package. let it install then go to system->Administration->windows wireless drivers then with the driver cd in, browse for the winxp drivers folder on the disc, then select the file with the .inf extension. if all goes well on the window it should say the drivers name and that the hardware is present.

---

### Post by Bailywolf on 2008-11-08
> **sc0tt10 said:**
> its only a five minute job, assuming you have access to a wired network on the laptop just search for ndisgtk and get the .deb package. let it install then go to system->Administration->windows wireless drivers then with the driver cd in, browse for the winxp drivers folder on the disc, then select the file with the .inf extension. if all goes well on the window it should say the drivers name and that the hardware is present.

I did this, but had to download the drivers from Linksys because I don't have a CD for the card, and...  every driver that came in the package for this card came up as "Invalid Driver" and wouldn't work.  If I snag the XP driver I have running the card right now (I'm posting from my XP install), will that work?  

Now, there IS a Linux driver available for this card from Linksys, but it's from five years ago, and there's nothing more recent.  Will Ubuntu work with a driver this old, and if so, how do I install a driver in Ubuntu?

-B

---

### Post by sc0tt10 on 2008-11-09
the one from the XP you're running should suffice, just as long as you have the .inf file

---

### Post by bonestonne on 2008-11-09
i find it strange that the wireless card doesn't work.

i have the same wireless card, and the same laptop, and it worked fine for me.

try this:
put the card into your laptop for a few seconds, pull it out, and put it back in.

after doing that, the card should work perfectly. i'm not sure if that'll help from then on, or not, but that should be the trick.

also remember to only use the bottom slot, as the top doesn't have pins (for whatever retarted reason).

---

