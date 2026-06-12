---
title: "Troube seeing HD (Pata to Sata Converter?)"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by MrMosier on 2009-08-14
I have a new Compaq that only has sata onboard. I was using a pata 320gb hd in my old machine to dual boot Ubuntu with XP. I am using a pata-to-sata converter for the pata hd, but it is not being recognized in Ubuntu. I want to install Ubuntu 9.04 on that hd. The other OS on the sata drive is Vista, and the other hd does show up in windows just fine. Any ideas?

***SORRY ABOUT THE MISSPELLED TITLE***

---

### Post by starcraft.man on 2009-08-14
Not a fan of converters to internal, I think they are a bit clugey. If ya ask me, my best advice I could give would be to buy a cheap enclosure for the old IDE and then use it as an external drive for storage. Then pick up any cheap sata drive ya can find and use that for installing OSes on. 

For example:
[Enclosure]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817106095")
[Internal Drive:]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075")

I know not everyone made of money, but IMO it's the best solution. Don't just go buy those two, was looking quick, I'm sure ya can probably get a better deal locally or searching a bit.

---

### Post by MrMosier on 2009-08-14
I am trying to use what I have. So far, this is the only issue at all. I am a teacher, so my funds for equipment are very limited.

---

### Post by starcraft.man on 2009-08-14
It might be your only issue so far, it is a pretty big issue though if your wanting to install to the HDD.

I'll reiterate that in my experience Linux supports IDE and SATA well (flawlessly tbh), it comes with the drivers needed. If ya provide me a link to product or just name and model I'll look into it but I make no promises. That it doesn't work as is with Linux, leads me to think it relies on something Windows for it's operation perhaps or is just poorly engineered. As I said before, in my experience, such converters are unreliable and not well made. I'm frankly a little surprised the board doesn't come with an IDE connector, most provide at least one on the side for legacy drives or floppy.

---

### Post by MrMosier on 2009-08-14
[http://www.microbarn.com/details.aspx?rid=101150](http://www.microbarn.com/details.aspx?rid=101150)
I have installed Ubunut, Debian, and several others, and this is one of the few times I have not been able to find a fix. The only legacy connector is for a floppy drive.
This is a link to the computer I bought:
[http://www.bestbuy.com/site/olspage.jsp?skuId=9371869&type=product&id=1218093382970](http://www.bestbuy.com/site/olspage.jsp?skuId=9371869&type=product&id=1218093382970)
As a worst case scenario, I could just leave it as Windows only (I have 3 other Linux machines already), but I would like to have a dual boot system.

I did not think of the floppy interface. I will check that this weekend and see if it works.

---

### Post by starcraft.man on 2009-08-14
Yes, I'd suggest trying the IDE Floppy connector, I don't think there's any reason it shouldn't work. I also thought of another solution. Using WUBI would bypass this problem I believe. It lets you install inside of Windows Ubuntu, it isn't exactly the same as installing directly to a partition. However, once installed to Windows by WUBI, the installation can in fact be transfered to the main hardrive via loopback mounting.

See [WUBI]("https://help.ubuntu.com/community/Wubi") (just pop it into Windows with any Live CD any it will run)
See [LVPM]("http://lubi.sourceforge.net/lvpm.html") for means to transfer to a free partition. NOTE: You need to have made one to move it to. Since the Ubuntu live partitioner doesn't seem to work, please try the [gparted]("http://gparted.sourceforge.net/download.php") live one here. Stable, and if that fails, testing. Partition should be at least 10GB, probably closer to 50 or so since I don't believe you can split the Home folder from the partition.

Hope that helps. As for the connector, I didn't find anything of interest. I don't believe anything terrible drastic happened to driver support in 9.04 to stop it working, unless it's a regression that was simply overlooked or untested. Might be worth a bug report on lp, if you've an account for further investigation.

---

### Post by MrMosier on 2009-08-15
Thanks for the idea. I have never used WUBI, and probably would have nevr considered it.

---

