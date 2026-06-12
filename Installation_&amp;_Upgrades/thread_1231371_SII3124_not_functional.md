---
title: "SII3124 not functional"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by jedmondson on 2009-08-04
Ok, I give up.
I've been searching for 2 days now and trying everything I find to get this darn SII3124 card to work at all with absolutely nothing happening.

Plenty of entries on how wonderful and linux friendly it is. :-(

I'm running the latest kernel: 2.6.28-14 on Ubuntu Server install and most of the entries I've found think that support is built in to the kernel but it isn't recognizing the card at all.
attempted to follow a couple of instructions on re-building the kernel, but can't locate sata_sil24.ko anywhere.

Can someone please help?

Thanks.

---

### Post by Mark Phelps on 2009-08-05
Being "wonderful and friendly", especially the latter, has nothing to do with manufacturers NOT providing Linux drivers for their controller cards. This continues to be the bane of Linux -- lack of drivers.

Sorry that you can't locate a driver for the SiL controller card, but I have two laptops that I had to "return" to MS Windows because of the same reason -- inability to find drivers that would work.

---

### Post by jedmondson on 2009-08-05
Allow me to clarify.
There is a Linux Driver, it is supported by libata, sata_sil24, and the latest kernel, however despite this and apparently nobody else ever having any problems it simply doesn't function at all for me.

It's not detected by ubuntu (which it appears it is for everyone else)

I can't find any decent instructions on how to manually get the sata_sil24 driver, or libata to work.  All the instructions I've found are very vauge and skip major steps.

---

### Post by Mark Phelps on 2009-08-05
Sorry, didn't know you already have the drivers ...

Don't know if you already have seen the link below, but it has a couple of FAQs linked to it that provide things you can check in BIOS settings and other stuff:

[http://linux-ata.org/driver-status.html]("http://linux-ata.org/driver-status.html")

---

### Post by jedmondson on 2009-08-05
NP,  ya that's actually where I first found out about it (since my old card wasn't supported) and thought: Wow great, one that is fully supported and everything works.  I should get that ;-)

---

### Post by jedmondson on 2009-08-31
Anybody have any suggestions?  still can't get it working.  Every website listing says it's fully supported and I shouldn't have to do anything, but it isn't recognized by Ubuntu.

Thanks.

Joe

---

### Post by kuritsubaji on 2010-02-03
I'm bumping up this old thread because jedmondson never got an answer and now I have a SiI3124RAID card that, I too, purchased because I thought I had found a RAID controller that was Linux compatible.  I have the same issue -- won't recognize the HDD.  Bad documentation; no driver; NOT PnP.  And where in the heck is sata_sil24?  What really sux is that I bought this card as an "open box" deal and if can't it to work, then I'm out 40 bux:(

---

### Post by jedmondson on 2010-02-03
I too am still interested in a response if anyone has had any luck.  I ended up giving up on using it for it's intended purpose, but still have the card and would like to be able to use it.

---

### Post by pirateghost on 2010-02-03
i use a few 3114 but no 3124 that i know of.  i am not sure if it uses the same drivers, but i have never had to do anything to make it work in any version of linux/bsd i have installed.

BUT

i do not attempt to utilize the raid function on the cards either, as i consider most of the bargain sata cards to be nothing more than port replicators,  i prefer linux raid over sil raid.

have you tried not using the RAID feature or am i way off base here and should shut up because the 3114 works so well and shares nothing with the 3124?

---

### Post by jedmondson on 2010-02-03
For my usage I don't want the RAID Functions, just need the eSATA connections to work.  For me with RAID off or on no devices plugged into it appear.

---

### Post by kuritsubaji on 2010-02-18
Same here...
I intended to just use it as an expansion because my mobo only has 4xSATA and I want to set up a 6x500GB RAID but using linux software RAID since, yes, most cards are just software RAID on a card with a big buffer. Still,  it can't find the drives.

I did send it back and pled incompatibility and got my $ back.  Until I can find a card that will work (that's not ridiculously expensive), I've got a 4x500GB RAID0 array using linux softRAID (mdRAID) and I get 400Mb/sec linear reads.

---

