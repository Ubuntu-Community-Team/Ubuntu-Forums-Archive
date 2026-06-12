---
title: "Thomson USB Wireless Adapter freezes my system"
date: 2008-07-29
forum: Hardware
---

### Post by AntoC on 2008-07-29
Hi guys,
I have recently installed Ubuntu 8.04 on a Inspiron 2500 laptop. I think that the Ethernet is physically broken therefore i have decided to use an old USB Wireless adapter. This dongle is equipped with a Silicon Integrated Systems Corp. chip and in two words the system does not recognise it as a wireless adapter. I tried to install it with the windows (oi!) wireless drivers through ndiswrapper and something strange happens:[LIST=1]
[*]The adapter is recognised as a wireless resource
[*]Is correctly installed as wlan0 and recon by the system
[*]Either if is installed in roaming mode it doesn't find hotspots
[*]When i attempt to connect manually to a hotspot it crashes my system..
[/LIST]
Has anyone experienced this issue?
The device is [this and it works in windows 2K]("http://www.wireless-driver.com/download/other/THOMSON-WLG-1500A-USB-54M-WLan-Driver.htm").


Thank you in advance for your help...

Forgot to say the chip: sis163u

---

### Post by AntoC on 2008-07-29
the command

```
iwlist power
```

yields:

lo no power mangement information

wlan0 Current mode:off

How to turn it on?

---

### Post by coffeecat on 2008-07-29
Hi.

I have absolutely no experience of this wireless adaptor, but I hoped a couple of comments might be helpful.

> **AntoC said:**
> Silicon Integrated Systems Corp. chip

#-o

Enough said? :(

But to be constructive. I did a google for 'sis163u' with or without 'Ubuntu' using [www.google.com/linux]("http://www.google.com/linux") (a useful version of google - did you know about it?) and came up with a lot of threads from other forums with similar issues to yours, but all unresolved. [This was the only one]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,27/func,view/catid,2/id,1435/") from an admittedly brief search that offered a ray of light - but that would mean using openSUSE. But you might find something of use if you did a similar search.

One other suggestion: you could use a usb-ethernet adaptor. Most, if not all, work ootb with Linux. I bought one a couple of years ago for an old laptop that had no ethernet port. Although the product details said Windows only or words to that effect (there was also a Windows driver CD in the box) it 'just worked' with Ubuntu Dapper. They're not very expensive.

---

### Post by AntoC on 2008-07-29
Hi coffe cat thank you for answering, thank you for pointing out the linux google version...
Still i would like to use this dongle, it seems like other people managed it...
Through if config i managed to set the power on but still it won't scan and if i try to manually connect it will freeze...

---

### Post by AntoC on 2008-07-29
Ok update,
the card is located correctly by the kernel, ifconfig shows it, iwlist wlan0 scanning says --no scan results---, iwconfig sees it as an adapter correctly, so it should work.....BUT
if I try  and connect the entire system crashes!!!....
at the same time the site [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/#t") says that people with the same card (id: 0457:0163) have had better luck.

No one?

Antonio

---

