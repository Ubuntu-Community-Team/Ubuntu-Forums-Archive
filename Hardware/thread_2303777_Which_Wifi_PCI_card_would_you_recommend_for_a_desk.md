---
title: "Which Wifi PCI card would you recommend for a desktop PC?"
date: 2015-11-21
forum: Hardware
---

### Post by naomibrown on 2015-11-21
I've got an old desktop PC which I would like to give wireless capacity because at the moment I'm tripping over cat 5 cable which is between my router and the computer. From what I've read (please correct me if I'm wrong) it would be better for me to use a PCI card rather than a USB wireless adapter because it would be quicker, more reliable and would leave me with more free USB connections. 

Which PCI card would you recommend for a desktop PC running Ubuntu 14.04?

I've looked at: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") and found one that looks likely at: [Penguin Wireless N Dual-Band PCIe Card for GNU / Linux TPE-N300PCIED (/w full & low profile brackets)]("Penguin Wireless N Dual-Band PCIe Card for GNU / Linux TPE-N300PCIED (/w full & low profile brackets)")

Are there any others that could do the job? [http://www.eclipsecomputers.com/product.aspx?code=NEA-PCEN15]("http://www.eclipsecomputers.com/product.aspx?code=NEA-PCEN15")

Some people seem to suggest that it is useful to have the same brand card as the router. Is this necessary? 

Is there a maximum distance that these cards can reach? I'm guessing that this will be different depending on the card.

Thanks! 
Naomi

---

### Post by weatherman2 on 2015-11-21
My recommendation is not to use either a PCI card or a USB wireless card.

Instead, use a wireless ethernet bridge - this is what I've been doing the last few years and it has worked really well.  Basically, the device connects wirelessly to your main router and then you just plug your ethernet cable from the desktop PC into the bridge's ethernet port.

Some wireless routers - an additional router, I mean, not the existing wireless router you already have - can be turned into wireless eithernet bridges with the factory firmware, but if the additional router supports an open source firmware like Tomato or DD-WRT, you will have more options.

My best experiences have been buying Broadcom-based Cisco/Linksys or Asus routers used, putting Tomato on them, and then using that router as a wireless ethernet bridge.  My local thrift store seems to have cheap deals on some good routers that have worked beautifully for this.  Before buying one, if I'm not familiar with the model number, I make sure on the Tomato firmware site (I prefer Shibby's (a Tomato developer's) Tomato versions) and make sure the router is compatible with Tomato.  But I know certain routers work great, like the Linksys E2000 (dual band 802.11n but not simultaneous dual band) or the Linksys E3000 (true dual band, but you don't need that for a wireless ethernet bridge).  My main router is another E3000 and I use 5GHZ 802.11n for the wireless ethernet bridge, and I'm able to stream videos on my desktop downstairs very well, for hours usually without any interruption.

Another benefit of a wireless ethernet bridge is that you can Wake-On Lan (WOL) remotely if you need to if you leave the router on.  You can't do this with a conventional wireless card on a desktop PC.  I do use this feature all the time to turn on my wireless desktop PC.

---

### Post by kurt18947 on 2015-11-22
For any fixed device (not a laptop or phone) I too prefer wired to wireless. I use MoCA and repurposed  routers. We already had the MoCA network because or cable company/ISP uses it with their 'cable boxes'. The numbers don't look especially impressive, <200 mb./sec. but as that capacity is pretty accurate. WiFi in my experience won't come close to claimed transfer rates unless everything is pretty optimal - little 2.4 ghz. interference, no structure that is wifi unfriendly such as steel reinforced concrete, thick masonry etc.  No broadcast network signal seems like one less point of vulnerability.  Could you re-route the cable that's in the way under carpets, along or under baseboards, use a something like a [floor cable protector?]("http://www.uline.com/Product/Detail/H-4127BL/Extension-Cords-Surge-Protectors/Cord-Protector-5-Standard-Black?pricode=WY596&gadtype=pla&id=H-4127BL&gclid=CPWa3pO2pMkCFUOQHwodJuIFPg&gclsrc=aw.ds")

---

### Post by naomibrown on 2015-12-18
Thanks for all the advice! I eventually went for the cables option ... :)

---

