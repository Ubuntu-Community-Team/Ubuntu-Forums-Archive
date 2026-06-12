---
title: "Need video card that works with Ubuntu 10:10"
date: 2011-02-11
forum: Hardware
---

### Post by Jon Anderson on 2011-02-11
I have a VIA/s3g graphic unichrome pro with k8m800 via chip-set Video card on my mother board of my old emachine t3104. But I am having a very hard time getting advice or help with the drivers for this video card(freezes up and I have to turn off the Compute, then reboot) so I'm thinking about getting the least expensive Video card that will work in my emachine in Ubuntu10:10. I'm looking for suggestions. As bad as this card is, I've not needed one any bette, so the video card doesn't have to be fancy, I think the word is cheap.

---

### Post by mastablasta on 2011-02-11
ATI/AMD or nVidia. for newer cards nVidia as they are supposedly have better proprietary drivers. but if you are buying an older card then ATI is also good as their opensource drivers are ok.

---

### Post by bigcreturns on 2011-02-11
Any feedback on the following video card for Ubuntu 10.10. I have heard about the dreadful freezing issues of the Fermi cards in the past.
**[SIZE=2]ASUS ENGT430/DI/1GD3(LP) GeForce GT 430 (Fermi) 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP [/SIZE]**

---

### Post by cascade9 on 2011-02-11
> **Jon Anderson said:**
> I have a VIA/s3g graphic unichrome pro with k8m800 via chip-set Video card on my mother board of my old emachine t3104. But I am having a very hard time getting advice or help with the drivers for this video card(freezes up and I have to turn off the Compute, then reboot) so I'm thinking about getting the least expensive Video card that will work in my emachine in Ubuntu10:10. 

Bad news... That system only has a AGP (and possible PCI slots) free, not the PCIe slots used by more modern machines. 

[http://emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3104](http://emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3104)

Depending on your country, and what sort of access you have to 2nd hard parts will make a bit of a difference as to what card to get. 

If you only have the option to get a new card, probably an nVidia 6200 is your best choice. In a lot of cases, its probably your only choice.

> **bigcreturns said:**
> Any feedback on the following video card for Ubuntu 10.10. I have heard about the dreadful freezing issues of the Fermi cards in the past.
**[SIZE=2]ASUS ENGT430/DI/1GD3(LP) GeForce GT 430 (Fermi) 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP [/SIZE]**

I havent heard of any major issues. 

BTW, you would do better to start your own thread, rather than hijacking this one. It wouldnt normally be quite so bad, but the OP will need an AGP card. Discussing new PCIe cards at the same time as older AGP cards is asking for confusion.

---

### Post by Jon Anderson on 2011-02-11
Yes, your right it has to be a AGP card, so do you still like the cards listed? Are they AGP cards

---

### Post by Jon Anderson on 2011-02-11
I guess I don't completely understand what you are saying. Can I get a cheap AGP card for my emachine T3104

---

### Post by bigcreturns on 2011-02-11
> **cascade9 said:**
> Bad news... That system only has a AGP (and possible PCI slots) free, not the PCIe slots used by more modern machines. 

[http://emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3104](http://emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T3104)

Depending on your country, and what sort of access you have to 2nd hard parts will make a bit of a difference as to what card to get. 

If you only have the option to get a new card, probably an nVidia 6200 is your best choice. In a lot of cases, its probably your only choice.



I havent heard of any major issues. 

BTW, you would do better to start your own thread, rather than hijacking this one. It wouldnt normally be quite so bad, but the OP will need an AGP card. Discussing new PCIe cards at the same time as older AGP cards is asking for confusion.

Oops. I did not see the AGP part.

---

### Post by quadproc on 2011-02-11
> **Jon Anderson said:**
>  I'm thinking about getting the least expensive Video card that will work in my emachine in Ubuntu10:10. I'm looking for suggestions.
Probably best to avoid ATI cards because there is a big issue with X windows having drastically changed the way that it works at about Ubuntu 8.10 -> 9.04.  ATI put their older cards on legacy status at about that time, and the drivers presently available from ATI do not support older cards. You cannot use an older ATI card with newer Ubuntu releases, period.

Also, there is an upcoming issue which will further muddy the waters - Ubuntu will discontinue X windows in favor of Wayland.  This will probably happen in about 1 year.  It is too soon to tell what the ramifications of that change will be.

quadproc

---

### Post by cascade9 on 2011-02-12
> **Jon Anderson said:**
> I guess I don't completely understand what you are saying. Can I get a cheap AGP card for my emachine T3104

Yes. AGP is obsolete, so what cards you can actually buy might vary. Generally nVidia 6200 AGP cards are available. 

> **quadproc said:**
> 

Probably best to avoid ATI cards because there is a big issue with X windows having drastically changed the way that it works at about Ubuntu 8.10 -> 9.04.  ATI put their older cards on legacy status at about that time, and the drivers presently available from ATI do not support older cards. You cannot use an older ATI card with newer Ubuntu releases, period.

No. 

The ATI cards that have had support discontinued will still work with ubuntu, just you cant use the proprietary drivers. They do work with the open soruce drivers.  

> **quadproc said:**
> Also, there is an upcoming issue which will further muddy the waters - Ubuntu will discontinue X windows in favor of Wayland.  This will probably happen in about 1 year.  It is too soon to tell what the ramifications of that change will be.

quadproc

If ubuntu goes to wayland in 1 year, there is going to be major problems. I doubt it will happen anywhere near that soon. 

If/when wayland does start being used, nVidia is probably the worst choice.

---

