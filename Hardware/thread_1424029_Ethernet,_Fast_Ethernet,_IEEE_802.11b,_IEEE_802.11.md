---
title: "Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g, IEEE 802.11n"
date: 2010-03-07
forum: Hardware
---

### Post by pingu1 on 2010-03-07
I am checking out a laptop and all the specifications say about wlan is:
Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g, IEEE 802.11n.

This does not say anything about what kind of wlan-card this computer has, does it?
From what I understand this just says it's got a WLAN-standard called "IEE 802.11", am I right?

Can anybody please explain to me what this information really tells me, and - will this WLAN-card work with Ubuntu 9.10?

---

### Post by 2hot6ft2 on 2010-03-07
> **pingu1 said:**
> And last question:
I am checking out a laptop and all the specifications say about wlan is:
Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g, IEEE 802.11n.

This does not say anything about what kind of wlan-card this computer has, does it?
From what I understand this just says it's got a WLAN-standard called "IEE 802.11", am I right?

Can anybody please explain to me what this information really tells me, and - will this WLAN-card work with Ubuntu 9.10?
That tells you that it has a b/g/n card but not what the cards mfg. is or the chipset that it uses. 802.11 is just the standard.

If it has windows.
Right click on the My Computer, or Computer icon
Select Manage
Select Device Manager
Expand Network Adapters by clicking on the + sign to the left of it.
That's where it will tell you the card it has and if you select it and right click then select Properties you can find out what driver it uses in windows.
Then you will have some info to find out if it will work in ubuntu.

---

### Post by pingu1 on 2010-03-07
Yes. The device list in windows would be great to check which card it has, unfortunately I don't know anyone who has this computer - so I am therefore asking - because I am seriously considering in investing a computer:
[http://www.komplett.no/k/ki.aspx?sku=576433&view=detailed#ProductTabs](http://www.komplett.no/k/ki.aspx?sku=576433&view=detailed#ProductTabs)

it's a " HP Compaq Presario CQ71-420".

---

### Post by 2hot6ft2 on 2010-03-07
> **pingu1 said:**
> Yes. The device list in windows would be great to check which card it has, unfortunately I don't know anyone who has this computer - so I am therefore asking - because I am seriously considering in investing a computer:
[http://www.komplett.no/k/ki.aspx?sku=576433&view=detailed#ProductTabs](http://www.komplett.no/k/ki.aspx?sku=576433&view=detailed#ProductTabs)

it's a " HP Compaq Presario CQ71-420".
There are 7 models that match that number here:
[URL="http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-002&h_query=HP+Compaq+Presario+CQ71-420&submit.x=9&submit.y=5"]Product search results Software & driver downloads
[/URL]
```
Results for "hp compaq presario cq71-420" (7 products)
	Compaq Presario CQ71-400 Notebook PC series	
		» Compaq Presario CQ71-420ED Notebook PC
» Compaq Presario CQ71-420EK Notebook PC
» Compaq Presario CQ71-420ER Notebook PC
» Compaq Presario CQ71-420EW Notebook PC
» Compaq Presario CQ71-420SF Notebook PC
» Compaq Presario CQ71-420SM Notebook PC
» Compaq Presario CQ71-420SO Notebook PC

```
The last 2 letters of the model # are on the label on the bottom of the computer.

By looking at the first one in the list under drivers for windows 7 32 bit here :
[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=4062&lc=en&dlc=en&cc=us&product=4131631&lang=en"]The following software and drivers are compatible with your product and the operating system Microsoft Windows 7 (32-bit)
[/URL]
 it shows:
```
Driver - Network	Date	Version	Previous	Size
» Intel PRO/Wireless Drivers for Microsoft Windows 7
	02-2010	13.1	» Version:	13.11M
» Broadcom Wireless LAN Driver for Microsoft Windows 7
	01-2010	5.60.48.18	» Version:	20.66M
» Atheros Wireless LAN Driver for Microsoft Windows 7
	12-2009	1.00	-	20.77M
```
So there's no telling which one it has. I would call the retailer and find out before even considering buying one.

---

### Post by cascade9 on 2010-03-07
After poking around the HP/Compaq site, it looks like that model supports freeDOS which is a sort-of good sign. Pity that they dont put the actual hardware specifications up- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01994744&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4131631](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01994744&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4131631)

I would guess that it is onboard intel wireless, which should work...but without the specs its a pure guess.

---

### Post by 2hot6ft2 on 2010-03-07
If it turns out to have an Atheros AR5009 wifi card then it will use the AR928X chipset and mine works fine so now you just need to find out what it has.

---

### Post by pingu1 on 2010-03-07
I found further down the site that the specific model I am considering is a 
"Compaq Presario CQ71-420SO"

Thanks for quick responses....

---

### Post by pingu1 on 2010-03-07
Increadable! HP doesn't even list what the wlan card is on the specifications on their website for the SO-mordel....

---

### Post by pingu1 on 2010-03-07
one site listed "Integrert 10/100BASE-T Ethernet LAN"... not sure if that is the actual card?

---

### Post by 2hot6ft2 on 2010-03-07
> **pingu1 said:**
> I found further down the site that the specific model I am considering is a 
"Compaq Presario CQ71-420SO"

Thanks for quick responses....
That one shows that there are 3 possible wifi cards for it. The other is the Ethernet.

---

### Post by pingu1 on 2010-03-07
Thank you!!
That helps a lot!

---

### Post by pingu1 on 2010-03-08
I think I can take a wild guess - and say that this computer has a 90% chance of working "out of the box" (meaning - find the right drivers - everything works).

Anybody agree with me? Although I think I will try it with a live-cd....

---

### Post by pingu1 on 2010-03-08
Is this such a new computer that nobody has this one?
Anybody got the same computer but different type/model.... (2 last letters of the model-name)
The computer I'm asking for experience with: 
Compaq Presario CQ71-420SO

---

### Post by pingu1 on 2010-03-10
I asked HP support for a "thumbs up" for use with Ubuntu 9.10. They googled, and found some answers I was not able to find - and apparantly the problem with this computer, is _not_ wlan - but sound. But there are several fix-methods out there. 

So I think - if anyone else consider buying this computer - you're pretty safe I would guess. I think I will buy it when I can afford it.

---

