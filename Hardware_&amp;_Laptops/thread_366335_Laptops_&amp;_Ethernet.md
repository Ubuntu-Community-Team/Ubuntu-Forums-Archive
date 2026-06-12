---
title: "Laptops &amp; Ethernet"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by pheebs on 2007-02-20
Hello again,

I'm happy to say that I have successfully installed Ubuntu on my Laptop, and everything is working seamlessly, except for the Internet.  The Laptop itself does not have an Ethernet port because it was purchased in the dial up days.  So I thought a USB adapter would solve the problem, but after purchasing one I figured out it wasn't supported by Linux.  Now I'm trying to find a different adapter or "card" that will allow me to connect to the net.

Here's two pictures of the Laptop slot that I thought could hold the cards listed below:
[LIST]
[*][Pic 1](http://img151.imageshack.us/img151/3761/dscf0848ek7.jpg)
[*][Pic 2](http://img246.imageshack.us/img246/3151/dscf0849ra3.jpg)
[/LIST]

And here are some products I was considering:

[LIST]
[*][Card 1](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=308770&CatId=588)
[*][Card 2](http://www.newegg.com/Product/Product.asp?Item=N82E16833328001)
[*][USB Adapter 1](http://www.newegg.com/Product/Product.asp?Item=N82E16833129104)
[/LIST]

I would truly appreciate this help so I can eventually start to really use Ubuntu.
Thanks

---

### Post by Strider on 2007-02-20
Hi,

The TrendNet is supported based on their support site ([http://www.trendnet.com/support/linux.htm](http://www.trendnet.com/support/linux.htm)) - take a look for TE100-PCBUSR.  I have a Dlink DFE-690TXD (retails for around $20-$30) and it works fine in several laptops I've used.  Driver comes default so I don't need to install anything.  Just make sure PCMCIA services is started and you should be fine.

Good luck!

-Mike

---

### Post by pheebs on 2007-02-20
Hey Mike!

If those slots on my laptop are for those type of cards, I'll look further into the Dlink one.  Thanks for your help.

---

### Post by Strider on 2007-02-20
What type of laptop is it?  Check the specs with the manufacturer to verify it's a PCMCIA slot (I'm pretty sure it is).  Depending on how old it is, it'll either be 16-bit or 32-bit.  Depending on if it's 16-bit or 32-bit, make sure the PCMCIA network adapter your purchase is compatible with it.

-Mike

---

### Post by pheebs on 2007-02-21
I went to

[This Site]("http://www.bixnet.com/vaiopcgfxa53.html")

Which lists replacement parts for the specific model of laptop (pretty handy).  All of the card adapters listed on the site are 32 bit, so I think that will work.  Also, TRENDnet seems to have a good Linux support system (and good newegg reviews), so I may go with one of those.

Thanks for all your help :)

---

