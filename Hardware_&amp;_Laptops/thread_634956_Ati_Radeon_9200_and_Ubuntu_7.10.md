---
title: "Ati Radeon 9200 and Ubuntu 7.10"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by frodemt on 2007-12-08
Hi

My father is taking the leap from Windows XP to Ubuntu 7.10.

He has a AMD Athlon 64 3500 socket 939 system with 512 MB ram.

I am going to upgrade the ram with one more gigabyte of ram, so he ends up with 1,5 GB of ram.

He also have a Ati Radeon 9200 AGP videocard. I dont know if this is going to be a problem for ubuntu or not? Of course he want to use all the effects and the nice look from compiz fusion.

Will it be hard for me to set up the system with this card? Should I recommend him a new card? I dont think he will like spending more money on this computer than the ram modules.

Regards
Frode

---

### Post by Kubunteando on 2007-12-08
There should not be big problems to run Compiz with an ATI 9200.
The important question is what drivers suit better that ATI card:

- proprietary ATI drivers (check if your card is supported by the last version, mine is not)
- open source drivers

I use an ATI Moblity Radeon 9000, and the proprietary drivers were too buggy.
Plus they don't support yet AIGLX (bets way to use Compiz).
With this card Compiz works well using the Open Source ones.

So I would try first the Open Source ones (installed by default with Ubuntu). 3D HW acceleration should be working out of the box.

The only drawback of open source drivers is the TV-out is not working, so check if you need it.

---

### Post by frodemt on 2007-12-08
Thank you for your answer Kubunteando!

He does not need TV-out. He is a normal desktop user who only needs support for opening word-dokuments and surf the Internet.

His is working as a journalist, and get provided with a file that formats the standard way office word looks when he starts a new document. I dont know what the file is named, but you might understand what I am thinking about. Can he use this file in OpenOffice too?

---

### Post by Kubunteando on 2007-12-08
I have not used myself Template files in Open Office.
But the Open Office coming with Ubuntu 7.10, at least, list them (.dot files) in the list of possible files to open.

So there are chances that they will work. But there may be some features on the templates that are not imported 100% right. So it is better to try it and see how it behaves your template.

---

### Post by Yellow Pasque on 2007-12-08
> **Kubunteando said:**
>  (check if your card is supported by the last version, mine is not)
The 9200 isn't supported by proprietary drivers either. If all you're seeking is 2D and desktop effects, it should work well enough through the open-source "radeon" driver.

---

### Post by frodemt on 2007-12-08
> **Temüjin said:**
> The 9200 isn't supported by proprietary drivers either. If all you're seeking is 2D and desktop effects, it should work well enough through the open-source "radeon" driver.

Yes, no 3D needed. He is not mutch of a gamer either :lolflag:

---

### Post by cmp1988 on 2007-12-09
I have one of these, and for Compiz, they're decent.  Overall, they're average.  Best part is that I can get a comfortable 1024X768 resolution with refresh rate at 85 Hz.   The feel of Ubuntu using this card is considerably slower than the feel of Windows XP.  The Open Source drivers don't offer all of the acceleration features of this card, but they're good enough to do what you're talking about doing.   3D apps such as Compiz, Google Earth, and Celestia work pretty well for me.  Browsing the internet with Firefox, and watching flash vids seems choppy, but that's just me.   I personally have problems with the Flash Player stuttering on streaming videos such as Youtube, but that's me, not sure about others with similar setup.  

When it comes to using a computer, I'm a bit of a speed demon.  I prefer having the computer run as fast as possible.  I feel that the setup should be alright in terms of video card.

---

### Post by frodemt on 2007-12-09
> **cmp1988 said:**
> 
When it comes to using a computer, I'm a bit of a speed demon.  I prefer having the computer run as fast as possible.  I feel that the setup should be alright in terms of video card.

Yeah me too. I will test ubuntu at first to see how well it works. If it does not work as good as windows XP I will have to talk him over to buy a cheap NV-card like 6700 GS or something.

---

