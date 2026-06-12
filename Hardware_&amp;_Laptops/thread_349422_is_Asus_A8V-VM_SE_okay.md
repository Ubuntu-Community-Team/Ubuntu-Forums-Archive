---
title: "is Asus A8V-VM SE okay?"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by eeried on 2007-01-30
Hello,
I'd need to buy a new computer to replace my PII 400MHZ which is in excellent condition but a bit slow and limited of course.

I've looked up A8V-VM SE, but got no result here. This motherboard is different from  A8V-VM and others.
Chipset: Via K8M890 - Vt 8237A
Sound: Realtek Azalia CODEC: Realtek ALC660 (found a post on this)

LAN: Realtek RTL8201CL 10/100M LAN

here's the Asus page: [A8V-VM SE]("http://www.asus.com/products.aspx?l1=3&l2=15&l3=260&model=1524&modelmenu=2")

Alternatively I could get Asrock 939NF6G-VSTA (NVIDIA GeForce 6100) but it seems you need to compile a newer kernel to make it work. they say Ubuntu uses an old kernel, which accounts for some hiccups wity some motherboard (and this one isn't ver recent).

thanks!

---

### Post by hal10000 on 2007-01-30
I just searched some linux hardware databases and found nothing about Asus board (that doesn't mean it's not compatible, but you can't be sure)

For the ASROCK board i've found this, but I'm not sure if it's exactly the same than the one you mentioned above: [http://www.linuxquestions.org/hcl/showproduct.php?product=3636&cat=36](http://www.linuxquestions.org/hcl/showproduct.php?product=3636&cat=36)

I've recently bought this one, it's a similar price than the Asrock board and I can say it's perfect for running linux: [http://www.alternate.de/html/product/details.html?artno=GHEM11&showTechData=true](http://www.alternate.de/html/product/details.html?artno=GHEM11&showTechData=true)
I' sorry this is a german site but i guess you can see the specifications. (Price=69&#8364;~~55$ or something like)

---

### Post by Toontje on 2007-01-30
Infact, I'm just installing Ubuntu on my new Asus A8V-VM SE server

Is the MB OK? I don't know yet, but I noticed that the VIA chipset is not recognized by default and therefore (U)DMA is not active.
This means HD performance is bad (1500Kb/s)

I will have to find out how to compile a new kernel to add the VIA drivers.

My setup:
ASUS A8V-VM SE
AMD Athlon 64 3800+
2 GB PC400 DDR
1x 160Gb Hitachi PATA
1x 250Gb Hitachi PATA
1U SuperMicro 260W

---

### Post by hal10000 on 2007-01-30
@Toontje
Have you tried hdparm? If not do [COLOR="Red"]sudo hdparm /dev/yourdisk[/COLOR] (yourdisk=hda, hdb or whatever) and look for a line like ```
using_dma    =  1 (on)
```
if it set to off, try [COLOR="Red"]sudo hdparm -d1 /dev/yourdisk[/COLOR]

To get it work during boottime see this link: [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by Toontje on 2007-01-30
Yes, I did, but this is the output:

setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off)

This means that the IDE controller is not recognized.

I just installed kernel 2.6.19.2 with VIA PATA device drivers installed and now my HD's are running on top speed.

But unfortunately something is wrong now with my kernel-headers. I want to install VMware-server, but it complains that the kernel-headers cannot be found..........

---

