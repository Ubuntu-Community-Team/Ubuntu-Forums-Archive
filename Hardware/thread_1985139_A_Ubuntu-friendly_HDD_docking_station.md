---
title: "A Ubuntu-friendly HDD docking station?"
date: 2012-05-22
forum: Hardware
---

### Post by Bucky Ball on 2012-05-22
Hi all,

In the market for a docking station and curious generally.

What HDD docking stations do people use with Ubuntu and what success have they had? 

Bucky is after a dual-dock with e-SATA that will take 2.5 and 3.5 SATA drives. I have been looking at the [Ritmo CD-895]("http://ritmotech.com.au/onlineshop/product_info.php?cPath=21_44&products_id=571") which claims to work with Linux. It is a triple dock (one for IDE) and on special at a store nearby, but I'm a bit suspect about the brand. Never owned a Ritmo and not heard many good things. Otherwise, looks good. (The store has them for AU$29.) 

Have also noticed the [Channel+ Fudse30]("http://msy.com.au/product.jsp?productId=7366which") which doesn't mention Linux, but works without software with Win and Mac so shows some promise. This brand I've never heard of. Has slot for 3.5 and one for a 2.5 by the looks, though, so doesn't really fit my bill (looking for two 3.5 slots that will also take a 2.5 HDD).

Fire away ... ;)

---

### Post by ahallubuntu on 2012-05-22
My guess is that most of them will work fine in Ubuntu - with possible exceptions for drives larger than 2TB.

I have plugged numerous hard drive enclosures and adapter into Ubuntu machines over the years and they have all worked fine.  The only issue I've had is sometimes needing to get S.M.A.R.T. information over USB.  There are ways to tell the latest versions of Smartmontools to try different chipsets to get this information correctly, though.

I recently bought this one from Thermaltake/NewEgg:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071)

but I paid less than that after rebate.  Although it's only USB2, it has worked quite well for both eSata and USB drive access in Ubuntu.  And no PATA/IDE - it's SATA only.  But I have separate adapters that work for PATA...

---

