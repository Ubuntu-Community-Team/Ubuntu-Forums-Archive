---
title: "wireless hardware recommendations"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by aanderse on 2007-03-19
i was wondering if anyone had some hardware suggestions for me:

i have a 64bit desktop computer and i want to purchase a wireless router and network card.  what is a good router to get if i live in an apartment (safety from neighbors stealing signal), and if i have other wireless devices (like a nintendo ds, a laptop, etc...)?  and what is a good wireless network card for my desktop (100% free and open source driver, and it would be nice if it "just worked" with gnu/linux)?

if anyone has had some experiences with good hardware, and some advice i would really appreciate it.

thanks!!

---

### Post by NICU28 on 2007-03-19
Hi, I've had great success with Linksys WiFi cards/adapters and routers at home.  For a router I would suggest the standard [Linksys WRT54G]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034939789B07")

In my laptop I use a [WPC54G]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=8192100349B03")

I don't know for sure if all of their PCI or USB 802.11 adapters work well with Ubuntu, but I would assume that they use similar chipsets to the PCMCIA chipset I use.  With some adapters you may need to run the Broadcom firmware installer - BCM43xx.

---

### Post by DrOlaf on 2007-03-19
+1 for the WRT54G. What I especially like about it is that, if you are feeling adventurous you can re-flash it with an open source firmware that opens up a lot of extra functionality. Read one report of that [here]("http://www.wi-fiplanet.com/tutorials/article.php/3562391"). Of course, this will void your warranty, so think carefully before you go down this road. I flashed mine and it worked a treat for many years - I only gave it up because I upgraded to Verizon FIOS and they provided an integrated router/modem (yes I know it's not really a modem). Come to think of it, it's still in its box in the cellar. Ebay awaits....

If you are interested in cards that support FOSS drivers, there is a good resource [here]("http://linux-wless.passys.nl/") that lets you look up a huge list of manufacturers and find out to what extent their cards work with FOSS drivers. Based on that site, I bought an [ EDIMAX EW-7128G]("http://www.newegg.com/product/product.asp?item=N82E16833315041") from newegg. I like the fact that this card comes with an antenna on an extension cable, so that you can position it up on your desk and get a better signal. I put it in my daughter's edubuntu desktop and it runs great.

---

### Post by aanderse on 2007-03-20
i have a friend who has that router, looks good.  the list of wireless cards is huge!  this gives me more than enough options :)

thanks for the help!

---

