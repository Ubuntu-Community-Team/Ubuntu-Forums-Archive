---
title: "Ubuntu 9.10 or 10.04 eSATA Port Multiplier (PMP) compatibility"
date: 2010-05-31
forum: Hardware
---

### Post by b2dnz on 2010-05-31
Hi Guys

I'm wondering if anyone out there has found a decent eSATA card (preferably PCI-E) that **definately** works with 9.10 or 10.04 x86 or x64. The primary functionality that I need is for Port Multiplier (PMP) support as I have an 4bay eSATA enclosure with single eSATA plug

I bought a cheap Sil3132 card but found that it has an old BIOS and is for all intents and purpose unflashable as the BIOS Flash is not compatible with the update tool (go figure). It took several nights of head banging and trial and error testing/research before I was able to come to this conclusion. So at this point I would just like to buy something that I know works out of the box or with minimal tinkering (I'm not a noob but not an expert either :P)

Anyone out there had any luck so far. I'm prepared to spend up to $150 if anyone has personally verified that the card works...Thanks in advance

---

### Post by b2dnz on 2010-05-31
By the way I'm using one of these cases - 

[[COLOR="Blue"]_eSATA Enclosure_[/COLOR]]("http://www.pccasegear.com/index.php?main_page=product_info&cPath=177_287&products_id=11912")
 
And this is why I need it :P

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158895&stc=1&d=1275319116[/IMG]

---

### Post by swizman on 2010-05-31
This matches your specs:


[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115076](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115076)
 HighPoint RocketRAID 622 PCI-Express 2.0 x1 SATA 6.0Gb/s Controller Card 

From their Specifications:

Operating Systems Supported:
Windows 7, Windows Vista, 2008, 2003, XP, 2000 x64bit Edition
RHEL/CentOS, SLES, OpenSuSE, Fedora Core, Debian, Ubuntu
Mac OS X 10.4.x and above
FreeBSD up to 7.2

Features:
Port Multiplier support up to 10 Drives 


However, I did NOT personally verified that the card works !! And it is only $55.00, LOL.

---

### Post by b2dnz on 2010-05-31
hmmm... a SATA 6.0Gb/s card, well SATAIII spec is new so this should have proper support already in the BIOS, my Sil3132 has a BIOS from 2004!!! Maybe there is hope for me...thx I'll do some research and see if any local vendors do this (with return policy) :p

---

### Post by b2dnz on 2010-06-01
Checked out their support website

[[COLOR="Blue"]http://www.highpoint-tech.com/USA/bios_rr620.htm[/COLOR]]("http://www.highpoint-tech.com/USA/bios_rr620.htm")

They seem to have up to date drivers for all the common OSs and Linux distros going back ~4yrs....me like

I might give this a try, will advise how it pans out...Thanks

---

### Post by firewrks on 2010-06-01
This combo is working for me with 10.04 with 3x drives on the same port. 
[Rosewill RC-219 Silicon Image PCI Express eSata x2 NCQ non-RAID SATA II Controller Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132020")
[ICY DOCK MB561US-4S-1 Aluminum / Plastic 4 x 3.5" USB2.0 & eSATA Aluminum HDD Enclosure for Mac & PC ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817198044")
[SIIG 6.56 ft. eSATA to eSATA Cable Model CB-SA0211-S1]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812191017")

It is also pretty quiet.

---

### Post by benenglishtx on 2010-07-12
> **firewrks said:**
> This combo is working for me with 10.04 with 3x drives on the same port.

I'm considering doing something similar.  I have a spare SATA port on my (supposedly PMP-supporting) mobo, so I'm planning to plug the eSATA extender that comes with the Icy Dock into that.

My question is - What do you see?  Do you see the three drives as three independent drives?  Or do you see one drive that's the size of all three added together?

I'm assuming the latter, but I can't find any documentation to confirm it before I start buying parts.

Also, as an aside, I've read that it's possible to boot from an eSATA device.  Have you tried that?

Ultimately, I'd like to have one SSD as my boot drive and 3 2Tb drives for data storage.  If all four can sit in an eSATA-connected external enclosure, allowing me to remove parts from my underpowered and extremely crowded small form factor computer case, that would be fantastic.

TIA for any thoughts.

ben

---

