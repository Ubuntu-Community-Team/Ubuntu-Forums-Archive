---
title: "ubuntu 10.04 hp pavilion dv4 - bluetooth"
date: 2011-11-06
forum: Hardware
---

### Post by andyubu on 2011-11-06
Hi everyone:

I bought a Hp Pavilion dv4 about 4 months ago - it came with Win7 and bluetooth. 

I installed Ubuntu 10.04 immediately after that, for some stupid reason, I screwed up the windows partition. As I rarely use Windows, I just let it go.

Now, I can't enable Bluetooth within Ubuntu. The only solution I found is to reinstall Win 7 then enable Bluetooth from within Windows.

1) Is there any way to enable bluetooth from within Ubuntu? 
2) Is there anyway to reinstall Win 7 without buying a new copy? (I have other laptops running Win7, just wonder if I can make a copy of Win7 from the other laptop and install on this one? If this is possible, how can I make it recognize all the hardwares?

Other info:

BIOS settings: 
Bluetooth FCC Id: PPD-AR5B195-H (don't know what it means, but something related to bluetooth?)

From the specs of the product 

Networking
Ethernet Port          10/100/1000
Integrated Wi-Fi       802.11b/g/n
Integrated Bluetooth   Yes


$hciconfig

hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:3 acl:0 sco:0 commands:1 errors:0
(it seems that the builtin bluetooth is not recognized)


Thank you very much

---

