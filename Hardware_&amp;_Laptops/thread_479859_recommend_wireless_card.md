---
title: "recommend wireless card"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by tronica on 2007-06-20
I need a wifi card for my laptop, I have two options, PCMCIA or mini pci. I've heard intel is veryl well supported.  But which one do i get. I found this one on newegg

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006](http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006)

the reviewer said it was a breeze with linux. also i would like one that is supported well with any distro.

---

### Post by tronica on 2007-06-20
anyone? what about a intel PRO/Wireless 2200BG? are they well supported

---

### Post by Syke on 2007-06-21
The 2200 should be well supported. I would go for mini pci first and save the pcmcia slot for other stuff later.

---

### Post by SendDerek on 2007-06-21
I would also go with a miniPCI.  I did that on my last computer that didn't have wireless built-in and it worked like a charm.  There are no things sticking out of the side of your laptop ready to be broken off or anything.

I use the Intel 3945abg wireless card and I really like it.  Good range and it has been recognized by network-manager since dapper.  Feisty installed it perfectly the very first time out of the box.

---

### Post by Platypi007 on 2007-06-21
yeah, I am wanting to replace my very unsupported factory installed Atheros AR5007EG card with something...  (sad, because the Atheros seems to have great range in windows.  But thus far neither ndisrapper nor madwifi support that particular card...)  and do not wnat a pc card sticking out.

I'll have to check these out.

---

### Post by tronica on 2007-06-21
do you think the 3945ABG is better than the 2200?

---

### Post by Syke on 2007-06-21
Yeah, if you can get a 3945, do it. That's a very supported card.

---

### Post by tronica on 2007-06-21
Awesome, thanks for the help guys.

---

### Post by Talon2 on 2007-06-21
> **tronica said:**
> I need a wifi card for my laptop, I have two options, PCMCIA or mini pci. I've heard intel is veryl well supported.  But which one do i get. I found this one on newegg

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006](http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006)

the reviewer said it was a breeze with linux. also i would like one that is supported well with any distro.

You do have a third option:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127053](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127053)

I use one.  The big benefit is you can move this device from system to system without reconfiguration.  Ubuntu doesn't even know it is running wirelessly.

---

### Post by stchman on 2007-06-21
> **tronica said:**
> I need a wifi card for my laptop, I have two options, PCMCIA or mini pci. I've heard intel is veryl well supported.  But which one do i get. I found this one on newegg

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006](http://www.newegg.com/Product/Product.aspx?Item=N82E16833150006)

the reviewer said it was a breeze with linux. also i would like one that is supported well with any distro.

Either Atheros or Intel(3945 or earlier).

---

### Post by Platypi007 on 2007-06-22
> **stchman said:**
> Either Atheros or Intel(3945 or earlier).


Do NOT get the Atheros AR5007EG, however.  It is unsupported in MadWifi at the present time.

---

### Post by stchman on 2007-06-22
> **Platypi007 said:**
> Do NOT get the Atheros AR5007EG, however.  It is unsupported in MadWifi at the present time.

Here is a compatibility list of Atheros based wifi cards.

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Yes the 5007EG does not seem to be supported at this time.  I have a 5006EG which is supported by Feisty out of the box.

---

### Post by tronica on 2007-06-22
i have an atheros card now, a ar5005g, it works with ubuntu, but not with fedora and some others. i need it to be all around compatible. And intel seems to be the one, i think i will go with the 2200G.

---

### Post by pickarooney on 2007-07-14
I need to get some sort of wireless solution for a gericom laptop. I don't know how to install a miniPCI card and would prefer something that I could remove quickly and switch to another PC. USB seems like it would suit me best, but I've no idea how to find one that will work with a minimum of messing about. Should I find the name of one that definitely works and hunt for that, or check the list of easily available USB adapters and try find out if it works? 
I've been comparing all the cards on offer on amazon.fr against the [compatibility list](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) but have yet to find a match. Also, I'm confused as to why the prices range from <&#8364;20 to over &#8364;60 for what appears to be pretty much the same thing?

Is anyone using a USB WiFi adaptor they would recommend and could tell me where they got it?

---

