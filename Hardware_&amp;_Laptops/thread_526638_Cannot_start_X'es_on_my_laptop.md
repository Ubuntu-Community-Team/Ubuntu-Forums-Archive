---
title: "Cannot start X'es on my laptop"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by macmus on 2007-08-15
Hello for first time on forum

I want to install Ubuntu on my laptop. I've DL the ubuntu 7.04 from website and when i start it strait from CD .. gnome does not come up. From xorg logs i can see ( using grep EE )

[EE] VESA(0): No matching modes 
[EE] Screen(s): found but none have usable configuration 

my computer is o Toshiba Satelite A210 with panoramic WXGA 1280x800 and inside it contains:

AMD 64 x2 TL-58 
grafic card ATI HD2600 

how can i start gnome on that hardware laptop ?

And then how can i install system on my HDD. I already got one free partition for that but i do not know how to start the instaler :( ( grub, lilo or something like that :) )

I look forward your help as i wanna join Ubuntu community :)
Thank you in advance.

---

### Post by dabl on 2007-08-15
Use the Alternate Install CD.  It will run in VGA/text mode.  When you are finished with the basic installation, you won't have a GUI.  Follow this to set up a VESA GUI display: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

Then you'll have to become a student of ATI and fglrx drivers to figure out a better driver for your ATI card.  :)

---

### Post by dougfractal on 2007-08-15
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4.html)

it looks like that ati haven't released a driver for your card

---

### Post by macmus on 2007-08-16
> **dougfractal said:**
>  looks like that ati haven't released a driver for your card
will then close one named "radeon" work at all to have compiz ??? 

i assume iif the aren't any driver from ati there is no sense in instaling fxgl driver and then making it xgl ?

till there are no driver only thing which left for me is 2d vesa ???

---

### Post by macmus on 2007-08-16
i found this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

does it mean my HD2600 is even not supported my default "radeon" driver ? :|

---

### Post by dougfractal on 2007-08-16
just googling your card for linux doesn't seem to turn up much,
try sabayon

---

### Post by macmus on 2007-08-16
> **dougfractal said:**
> 
try sabayon

what is that ?

---

### Post by dougfractal on 2007-08-16
[http://www.google.co.uk/search?q=sabayon&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=sabayon&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a)

its bleeding edge gentoo

---

### Post by macmus on 2007-08-16
ok so far i found out that ether open driver "radeon" and the **_Official_** one is not supporting the HD2600 series !!!!! 

CRAP ...

i should have bought a Nvidia laptop :((

---

### Post by dougfractal on 2007-08-16
it may get better in the future look out for **avivo** driver 

[http://www.phoronix.com/scan.php?page=article&item=715&num=1](http://www.phoronix.com/scan.php?page=article&item=715&num=1)> The AMD R600 series was originally scheduled for launch towards the end of last year, however, engineering problems had led to this multi-month delay. Phoronix had seen an earlier revision of the R600 in hand, which was especially interesting. However, these multiple delays have allowed additional time for the Catalyst development teams to fine-tune the R600 driver support. Since January we have been reporting that ATI/AMD has in fact been working on Radeon HD 2000 (or at the time, the Radeon X2000 series) product support. We seen the PCI ID entries initially in the 8.33 beta display driver and since then we know AMD has been working further on R600 generation support. Official support wasn't appended last month in the fglrx 8.36.5 driver and it will not arrive this month in fglrx 8.37 either. We do anticipate, however, that this support for the HD 2400, HD 2600, and HD 2900 in Linux will arrive shortly.

---

### Post by macmus on 2007-08-16
this new is posted in May :(
That does not foreseen a good future .. How can i instal avivo driver ? Currenly i have fedora 7 where i am experiencing the same problem ( open and closed drivers does not work :( ) Does avivo has designated package or should i compile it from sources ?

edit:

i found out avivo does not contain so far 3d acceleration possibility :(

---

### Post by dougfractal on 2007-08-16
I think you looking at atleast 6months before avivo is ready.

till then you will have to use:    driver "vesa"   :(

---

### Post by macmus on 2007-08-16
or wait for ati drivers to support hd2600 ...

i had a ati card in my laptop last time and had beryl :( ( it was x700 supported with open driver) now i will have to stick with vesa...

i hate ATI/AMd :((

next time will only buy nvidia/intel :(

---

### Post by atsab on 2007-09-17
Hey i had a similar  problem 
if you havnt already solved it
try this thread for a solution
[http://ubuntuforums.org/showthread.php?t=549217](http://ubuntuforums.org/showthread.php?t=549217)

---

