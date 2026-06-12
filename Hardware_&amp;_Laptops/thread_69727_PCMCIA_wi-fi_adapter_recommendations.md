---
title: "PCMCIA wi-fi adapter recommendations"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by ohzopants on 2005-09-27
I currently have a wi-fi card (D-Link DWL-650+), but it is a piece of crap.  It sorta works when it wants to and tends to crash my computer (it's performance is also crappy in windows).

I'm now looking to buy a new one and am looking for recommendations, essentially what I want is something that works WELL (in linux and windows).  I have pored over various posts about wi-fi cards but I've noticed that people only post when they have problems, no one posts about cards that work well...

I'm also wondering if USB wi-fi adapters are a viable option...

Any input is appreciated (even posts of the type DO NOT buy model X),
thanks

---

### Post by mlomker on 2005-09-27
> about wi-fi cards but I've noticed that people only post when they have problems, no one posts about cards that work well...


The problem is that companies like Linksys do not change the model number when they come out with a new card, the just change the **rev** to v1, v2, v3, etc.  Unfortunately those cards may use different chipsets that aren't compatible and you won't know until you open the box and look at the revision number on the card itself.  :mad: 

> 
I'm also wondering if USB wi-fi adapters are a viable option...


NO!  Stay away from them.

[This list is a little dated.]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")  I'd look for a card that is either Atheros or Prism54 compatible.  Everything works on the Windows side...no worries there.

---

### Post by spd106 on 2005-09-28
I've got a belkin F5D7010 rev 1 card, though it's detected as a ```
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```
As far as I am aware this card is no longer available since the belkin website also has rev 2 and rev 3 windows drivers. I would not recommend it anyway as it doesn't have native support in linux. It works fine with the ndiswrapper-utils package and has done since ndiswrapper v0.12. At least that's the first version I tried, way back with Warty.
I don't claim to be a expert in this field but I would expect that there won't be any major changes to chipsets on the cards till the IEEE 802.11n specs are sorted out (if ever) and we start to see the next generation of MIMO cards. We'll probably see only minor revisions and updates to existing technology in the mean time. I doubt that these so-called pre-n cards are really worth paying extra for unless you have bad reception issues or need more range.  
From reading these forums the best bet would be a atheros or prism based card. Though it might be tricky to find the one you want. I'm on the lookout for a new card as well, so if anyone has a good one please let us know.

---

### Post by AndrewB on 2005-09-29
I had nothing but grief from Linksys WG54 netcards.

However, The **Netgear WG511U**  Atheros chip set card if fantastic. It is very resource light in both W98SE and Ubuntu/Damn Small Linux. I'm using it in a 266M pentium notebook. Was ~$29 after rebate at Staples.

Andrew

---

