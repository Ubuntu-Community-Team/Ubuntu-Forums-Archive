---
title: "Splitter cables"
date: 2012-03-19
forum: Hardware
---

### Post by Homeground on 2012-03-19
I want to try to recover data from an old hard drive. I've got a laptop and a small-format desktop, neither of which can accommodate an extra drive. But if I open up the desktop and use splitter cables I could just rest the bad drive on top of the new one while I carry out the operation. I've looked on Amazon, and I can find any number of power splitter cables (pages of them), but I can't find any data splitter cables (SATA). Do these exist?

---

### Post by jerrrys on 2012-03-19
Just install the bad HDD and then try to access it with your Ubuntu live CD.

---

### Post by kurt18947 on 2012-03-19
> **Homeground said:**
> I want to try to recover data from an old hard drive. I've got a laptop and a small-format desktop, neither of which can accommodate an extra drive. But if I open up the desktop and use splitter cables I could just rest the bad drive on top of the new one while I carry out the operation. I've looked on Amazon, and I can find any number of power splitter cables (pages of them), but I can't find any data splitter cables (SATA). Do these exist?

AFAIK you can't have more than one drive on a SATA cable like you could IDE/PATA. You need one SATA data cable/drive. Another consideration is if you're able to access the bad drive you'll need some place to copy the contents to. Yet another consideration would be power cables.  Some 3.5" SATA drives have dual power connections, 4 pin molex and SATA power.  Others do not, they're SATA power only. You can get 4 pin molex -> SATA power cables.

---

### Post by Yellow Pasque on 2012-03-19
It's possible, but it's not cheap (because you need a port multiplier): [https://en.wikipedia.org/wiki/Port_multiplier](https://en.wikipedia.org/wiki/Port_multiplier)

---

### Post by varunendra on 2012-03-20
*@Homeground*,
Unless you have an extra SATA port on the desktop board, I think you are going to need a SATA to USB adapter. I believe (but can't say for sure) it should be cheaper that a port-multiplier.

---

### Post by kurt18947 on 2012-03-20
> **varunendra said:**
> *@Homeground*,
Unless you have an extra SATA port on the desktop board, I think you are going to need a SATA to USB adapter. I believe (but can't say for sure) it should be cheaper that a port-multiplier.

The usual fix (and the cheapest) is an external enclosure.  I have a couple <$10 enclosures for 2.5" drives and they work well.  On newer machines they only require one USB port though the cables usually come with two plugs. 3.5" enclosures require external power.  Another option if someone were swapping drives quite often is a dock.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=100006519&isNodeId=1&Description=hard+drive+dock](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=100006519&isNodeId=1&Description=hard+drive+dock)

---

### Post by Homeground on 2012-03-23
How about one of these:
[http://www.amazon.co.uk/exec/obidos/ASIN/B004ND4632/ref=ox_ya_os_product](http://www.amazon.co.uk/exec/obidos/ASIN/B004ND4632/ref=ox_ya_os_product)

---

### Post by kurt18947 on 2012-03-24
> **Homeground said:**
> How about one of these:
[http://www.amazon.co.uk/exec/obidos/ASIN/B004ND4632/ref=ox_ya_os_product](http://www.amazon.co.uk/exec/obidos/ASIN/B004ND4632/ref=ox_ya_os_product)

I haven't used one but it looks like it should work.  A couple things to bear in mind.  One is that USB 2.0 is going to be quite a bit slower than SATA but slow beats not-at-all.  The other is that the file system must be readable.  I presume these adapters would work with data recovery tools should that be necessary.

---

