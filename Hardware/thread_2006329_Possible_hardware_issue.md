---
title: "Possible hardware issue?"
date: 2012-06-19
forum: Hardware
---

### Post by jllipke on 2012-06-19
Hi, I'm pretty new to Ubuntu so bear with me... I am running Ubuntu 11.10 on VMware and when I go to connect it to the internet, it is always looking for a wired connection. I know I have a wireless card in my laptop. Is there a way to fix this?

I am running a Compaq Presario CQ60 if that makes a difference.
feel free to ask any questions

thanks, :)

---

### Post by typhoon_tip on 2012-06-19
> **jllipke said:**
> Hi, I'm pretty new to Ubuntu so bear with me... I am running Ubuntu 11.10 on VMware and when I go to connect it to the internet, it is always looking for a wired connection. I know I have a wireless card in my laptop. Is there a way to fix this?

I am running a Compaq Presario CQ60 if that makes a difference.
feel free to ask any questions

thanks, :)

You must install some sort of driver extension pack into your Ubuntu virtual machine. To do so, use the menu of VMWare once Ubuntu has started.

---

### Post by jllipke on 2012-06-19
I am running VMWare 6 if that makes a difference.

Do I need to install the VMWare tools?

---

### Post by Bucky Ball on 2012-06-19
Welcome.

I don't have any experience running Ubuntu as a VM but I presume once it's running it is like any regular install re updating.

Can you plug in a cable and get online? If so, then do an update and it might fix your wireless issue. Can you boot into Ubuntu and post the result of this (from a terminal: Applications> Accessories> Terminal):

```
sudo lshw -C network
```That will show if the card is recognised and what it is. Being online and an update will then help us install the appropriate drivers. A lot of the time you need to be online with a cable to setup wireless. Catch 22. ;)

PS: After an update go to 'Additional Drivers' and see what is there (for that matter, have a look there now).

---

### Post by jllipke on 2012-06-19
*-network               
         description: Ethernet interface
         product: 79c970 [PCnet32 LANCE]
         vendor: Hynix Semiconductor (Hyundai Electronics)
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 10
         serial: 00:0c:29:3c:44:ba
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master rom ethernet physical logical
         configuration: broadcast=yes driver=pcnet32 driverversion=1.35 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes
         resources: irq:18 ioport:2000(size=12 memory:40000000-4000ffff

---

### Post by Bucky Ball on 2012-06-19
Ok. The wireless card is not recognised (machine doesn't know you have a wireless card) but does look like your wired connection is good to go, both points explaining why it is going for that option. Is it possible to plug a cable in? Hard to know whether the card is dead without digging a bit deeper. 

I think there is one of those in the house but wouldn't do much good me checking that as there are millions of different ones in the series. 

[http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=321957&prodSeriesId=3768152](http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=321957&prodSeriesId=3768152)

Your details should be on a sticker on the bottom.

---

### Post by jllipke on 2012-06-19
I'll have to get my hands on an Ethernet cable which won't be much trouble.

you would think that ubuntu 11.10 being so new that it would have the proper drivers already in the install. 

I can assume that the updater will install those needed drivers, is that correct?

---

### Post by Bucky Ball on 2012-06-19
> **jllipke said:**
> ... you would think that ubuntu 11.10 being so new that it would have the proper drivers already in the install. 

This, unfortunately, has nothing to do with Ubuntu. It is about third-party manufacturers/hardware/firmware/software. For your card you may require firmware/software that you need to agree to the terms of use from the maker to use. If so, these wares cannot, by law, be contained in the install ISO. The manufacturer of your wireless card may have not even ported it to Linux at all so you would hope for an open-source driver solution. 

This is an ongoing issue. Linux/OpenSource/Developers have NO say over whether a manufacturer chooses to make their wares Linux compatible or share code with the community. Meanwhile, unpaid enthusiasts take things apart, write code and try to figure out how to get hardware working in Linux. 

;)

Yes, hopefully, presuming the card is not dead, the update will notice the card and, if not install it, will possibly offer you the correct drivers (which you will then have to agree to, etc ....).

---

### Post by jllipke on 2012-06-19
It's always something:)

Thanks,

---

### Post by Bucky Ball on 2012-06-19
Let us know how you go with the cable and update ...

---

### Post by jllipke on 2012-06-21
Ok, the problem has actually gone to an extent. Now my other VMs aren't connecting, even the ones that have connected in that form before. I don't think the problem got worse but it is defiantly further than Ubuntu.

---

