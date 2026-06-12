---
title: "Got a new lappy, need wireless card."
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2006-10-04
hi all. I finally got myself a laptop capable of runnig ubuntu. My last one (P233/64) was way too slow, so I used puppy before the wife stole it and insisted on windows.

So, now I have a Toshiba satellite pro 4300. Not new, but reasonable.
PIII 600, 384MB, 4GB. I need a wireless card for it, and I have been considering [this one]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ih=019&item=290017998036"), mainly because it mentions linux on the page, and I like the idea of an external antenna.

Is it a reasonable choice? Failing that, what would be a good one? I would prefer native drivers rather than that ndis thingy. :rolleyes:

---

### Post by fazavon on 2006-10-04
you can go with
 
[http://www.bestbuy.com/site/olspage.jsp?skuId=7442494&type=product&productCategoryId=pcmcat25300050003&id=1125238693506](http://www.bestbuy.com/site/olspage.jsp?skuId=7442494&type=product&productCategoryId=pcmcat25300050003&id=1125238693506)
 
it has the Prism2 chip set and uses the Broadcom 43XX Linux drivers. plus its cheep and it works great for me. ill even throw in the easy way to install for the low price of Free...

this one worked for me

1.2.2.2. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listsings and install the bcm43xx-firmware package.

or download the package directly:

wget -c [http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb](http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb)

and then install it manually:

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

Enjoy!!

---

### Post by xmastree on 2006-10-05
Thanks, but... $39.99 plus shipping(?), and they're sold out anyway.

Still, if I can find one locally I might go for it.

Thanks

---

### Post by fazavon on 2006-10-09
they have them in store i was just showing you the model..

---

### Post by xmastree on 2006-10-09
Thanks, I'll see if any UK stores carry it.

---

### Post by jml on 2006-10-09
The Oronoco Gold card is Linux compatible, but its only 802.11b.  So if you need WPA encryption, this card will not do.  Another card that I got to work with Ubuntu is the NetGear WG511T.  Its an 802.11b,g compatible card and Ubuntu recognizes it out of the box.  It also supports WPA wireless encryption.  

If you need WPA encryption, (as opposed to WEP which is supported out of the box,)  you will need to download an application called wpa_supplicant, and Network-Manager.  I'm told that this combination does work in Ubuntu, but to be frank, I have never been able to get it to work.  Hope this helps.

Joe

---

### Post by TheCan on 2006-10-09
If you want to use WPA, i suggest you try getting an Atheros-based Card (they're only available as 32bit PCMCIA afaik) - i once had once (Conceptronic C45RC - not C45RCi which is texas instruments chip or something) and it was quite good!

---

### Post by hw-tph on 2006-10-10
Do NOT get a Broadcom based card (like the bcm43xx mentioned). Broadcom does not support Linux with their WLAN products, even though the [bcm43xx project](http://bcm43xx.berlios.de) has managed to produce working drivers by now - several years after the chips were introduced.

Get an Orinoco card or anything from a vendor that supports Linux or at least provides full documentation for their products (so writing a good driver is possible and perhaps even easy).


Håkan

---

### Post by xmastree on 2006-10-10
> **jml said:**
> The Oronoco Gold card is Linux compatible, but its only 802.11b.  So if you need WPA encryption, this card will not do.
Well, I'm not really sure what WPA encryption is. AFAIK my home network uses WEP.

What about [**this**](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=220036472741) Orinoco Gold, which claims to be 802.11b/g... :confused: 

I've heard about Atheros based cards, but could only find miniPCI models.

---

### Post by xmastree on 2006-10-13
well, I appear to have won the Orinoco 802.11b/g so let's see if I can make it work...

---

### Post by zenwhen on 2006-10-13
> **xmastree said:**
> well, I appear to have won the Orinoco 802.11b/g so let's see if I can make it work...

It should work the moment you plug it in.

---

### Post by tturrisi on 2006-10-14
That orinoco card is a good one.  I use this one from the same seller because it has a better chipset (atheros):
[http://www.data-alliance.net/servlet/Detail?no=35](http://www.data-alliance.net/servlet/Detail?no=35)

---

### Post by xmastree on 2006-10-14
Yep, I'm looking forward to it 'just working' once I decide which flavour of ubuntu to go with.

---

### Post by unforeseen on 2006-10-14
I think you should check out this link before buying anything: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Seems to have a lot of valuable information :D

---

### Post by xmastree on 2006-10-20
> **xmastree said:**
> Yep, I'm looking forward to it 'just working' once I decide which flavour of ubuntu to go with.
Well, I have it and I think it's working, but how do I configure it?

Searching the forums lead me to try **iwlist scan** which yeilds promising results.

ath0 Scan completed:
Cell 01 - Address: [i]mac address[/i/
ESSID:BTomeHub-EA9D" (my hub)
Mode:Master
Frequency:2.412 GHz (Channel 1)
Quality=20/94 Signal level=-75dBm Noise level=-95dBm
Encryption key:on

So, it's seeing the hub, but how do I input the WEP key?

I'm running xfce, and can't find any fancy graphical tools, so it's command line stuff only please...


Edit: 
Woo Hoo, Got it!\\:D/ \\:D/ \\:D/

---

