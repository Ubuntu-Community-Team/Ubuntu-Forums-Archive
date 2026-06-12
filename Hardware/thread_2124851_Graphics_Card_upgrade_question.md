---
title: "Graphics Card upgrade question"
date: 2013-03-12
forum: Hardware
---

### Post by WierdKid on 2013-03-12
So after picking up The Witcher 2 for my desktop I discovered that the graphics card in it is woefully underpowered these days. I've decided to upgrade and will be sticking with ATI but I am at the limits of my knowledge trying to figure out the best route to take. The options I am considering are as such.

Option 1: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814103187]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814103187")
     It's a 6450 with 1GB of GDDR3, I'd pick up 2 and run them in Crossfire

Option 2: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814161427]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161427")
     It's a 7750 with 2 GB of DDR, it would run solo

Option 3: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814161402]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161402")
     It's a  7770 with 1 GB of GDDR5, also running solo.

I'm definitly looking for a big performance boost for The Witcher 2 (it runs on my ATI 4650, but it's not pretty), but I'm also looking to add some longer term power, as well as getting into a DX11 card. This is on my Windows 7 computer (but only until I can get more of my games working with Wine), and yes I am set on keeping it an ATI system. I appreciate any usefull advice on which route to take.

---

### Post by ManamiVixen on 2013-03-12
You REALLY should move away from ATI. Linux support from them sucks. Latest X.Org builds won't even run any ATI card due to fglrx failing. Hence why Ubuntu kept an older of X.Org version for 13.04 so you could buy an ATI card and have it run. But who knows what would happen in the near future. Because there was an article that came out a few months back that contained a statement by AMD/ATI stating certain cards "obsolete" that were only a few years old and such were no longer supported in the fglrx driver.

---

### Post by WierdKid on 2013-03-12
I'm not banking on anything staying consistent with drivers. I had a nightmare getting Ubuntu up in my laptop with Nvidea, and I've always had better gaming performance in my ati cards.

But brand arguments aside, which is the better route long term? GPU speed, memory amount, or parallel cards?

---

### Post by QIII on 2013-03-12
> **ManamiVixen said:**
> You REALLY should move away from ATI. Linux support from them sucks. Latest X.Org builds won't even run any ATI card. Hence why Ubuntu kept an older of X.Org version for 13.04 so you could buy an ATI card and have it run. But who knows what would happen in the near future. Because there was an article that came out a few months back that contained a statement by AMD/ATI stating certain cards "obsolete" that were only a few years old and such were no longer supported in the fglrx driver.

This is entirely incorrect.  QQ uses xserver 1.13 which, at the time, was the current one.  xorg announced that 1.14 was commited on March 6, 2013.  There are plenty of people, myself included, using ATI graphics in QQ.  The version will still probably be 1.13 in RR because the xorg release is so recent.  The cards that will not run on 1.13 are the cards that ATI sent along the legacy branch -- most recently HD 2xxx to HD 4xxx.

---

### Post by WierdKid on 2013-03-12
Thanks for that info. Any ideas in which route to take for my upgrade?

---

### Post by ManamiVixen on 2013-03-12
QIII, I was only saying what I knew. I never said it was right or wrong. I expect people to do some research on what I say rather than taking it to heart.

 But it is true, ATI has yet to update to X.Org 1.14. That could be a disaster in the making. Also, you pointed out the legacy cards. Those were the ones I was talking about were "obsolete".

---

### Post by QIII on 2013-03-12
This is more or less one of my areas of great interest, since I help maintain the wiki.

Since 1.14 was committed only a week ago, I suspect that it will be a bit before anyone, OEMs or distros, tests it thoroughly.

The legacy status of those cards has been discussed ad infinitum.  This is not news.  I have been talking about it on the forums for months.  I have even said myself that I am not happy with ATI's decision.  But it was their business decision to make and it was driven by market pressure, not some sort of dislike of Linux.  

AMD is a member of the Linux Foundation, by the way.

---

