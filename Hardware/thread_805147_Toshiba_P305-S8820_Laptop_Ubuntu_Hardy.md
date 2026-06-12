---
title: "Toshiba P305-S8820 Laptop Ubuntu Hardy"
date: 2008-05-23
forum: Hardware
---

### Post by stchman on 2008-05-23
Hello all, I have been looking at a laptop to replace my Toshiba A135-S2246.

Before you guys say Dell, I want a 17" screen and the Dell Ubuntu offerings have no 17" screen.

I have narrowed it down to the P305-S8820.  Here are the specs

Core 2 Duo
3GB RAM
Intel 10/100 LAN
Intel 3945ABG Wireless
Intel GM965 Chipset
Intel GMA X3100
Intel HD Audio
5 - 1 Media slot

As you can see the laptop is an Intel Centrino based model so everything should work.  The only thing that may not work OOB is the media reader.

I have read that Hardy supports the X3100 with Compiz now OOB.

Does anyone have any experience with this laptop using Hardy?  I plan on taking a LiveCD over to Office Depot and booting the PC up.

Thanks.

---

### Post by hotweiss on 2008-05-23
That's a nice configuration, minus the 4200 rpm hard drive. I'd take a look at this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220314&nm_mc=OTC-C173T&cm_mmc=OTC-C173T-_-Notebooks-_-ASUS-_-34220314](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220314&nm_mc=OTC-C173T&cm_mmc=OTC-C173T-_-Notebooks-_-ASUS-_-34220314)

It's similarly priced and offers a better video card, hard drive, warranty (2 years), Bluetooth, HDMI output, eSATA,free case, free mouse and 802.11n. Asus is coming out with some pretty competitive stuff now. I just purchased an M50Sv-A1 that I'm really happy with. They even give you a free one year accidental damage warranty.

Here's my Ubuntu Asus M50 install guide:

[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

---

### Post by stchman on 2008-05-24
> **hotweiss said:**
> That's a nice configuration, minus the 4200 rpm hard drive. I'd take a look at this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220314&nm_mc=OTC-C173T&cm_mmc=OTC-C173T-_-Notebooks-_-ASUS-_-34220314](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220314&nm_mc=OTC-C173T&cm_mmc=OTC-C173T-_-Notebooks-_-ASUS-_-34220314)

It's similarly priced and offers a better video card, hard drive, warranty (2 years), Bluetooth, HDMI output, eSATA,free case, free mouse and 802.11n. Asus is coming out with some pretty competitive stuff now. I just purchased an M50Sv-A1 that I'm really happy with. They even give you a free one year accidental damage warranty.

Here's my Ubuntu Asus M50 install guide:

[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

I went to Office Depot and brought my LiveCD.  The guy looked at me funny.

The 3945ABG wireless worked very spotty.

The Marvell 88E8040T ethernet did not work and Marvell has rotten drivers for that card.

The webcam worked with install of Cheese.

The 5 in 1 card reader did not work.

Compiz on the X3100 worked OOB.

I passed on it.

---

### Post by hotweiss on 2008-05-25
> **stchman said:**
> I went to Office Depot and brought my LiveCD.  The guy looked at me funny.

The 3945ABG wireless worked very spotty.

The Marvell 88E8040T ethernet did not work and Marvell has rotten drivers for that card.

The webcam worked with install of Cheese.

The 5 in 1 card reader did not work.

Compiz on the X3100 worked OOB.

I passed on it.

Check out the Asus. I can tell you that the wireless will work out of the box. There is a webcam driver for Ubuntu. Can't tell you anything about the LAN or memory card reader, as I haven't tried them yet. Here's my Asus M50 Ubuntu guide:

[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

For me the Asus warranty was the biggest plus.

---

### Post by stchman on 2008-05-26
I settled on the Toshiba A205-S5859.

Everything works OOB with Hardy except the Ti 5 in 1 card reader for Xd.  The reader works OOB for SD.  I am working on that.

Wireless, Ethernet, X3100 with Compiz, Webcam.

I recommend this laptop.

---

### Post by jdkchem on 2008-05-30
I am looking at the Toshiba Satellite P305D-S8818 from Newegg [http://www.newegg.com/Product/Product.aspx?Item=N82E16834114461](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114461).  Any information on compatibility with Hardy?

Thanks

---

### Post by stchman on 2008-05-30
> **jdkchem said:**
> I am looking at the Toshiba Satellite P305D-S8818 from Newegg [http://www.newegg.com/Product/Product.aspx?Item=N82E16834114461](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114461).  Any information on compatibility with Hardy?

Thanks

The laptop you chose has an Atheros card so it might work.  Also ATI cards can be a pain getting them to work in Linux.

I returned the P305 model Toshiba and got an A205-S5859.  The 3945ABG was flaky and the Marvell ethernet would not work on the P305 model.

The A205 model (which had pretty much the same hardware except a 4965AGN and a Realtek ehternet) worked OOB with Hardy.

I actually think Circuit City has better prices on laptops than the internet sites.  CC sells the laptops at a loss as they make up that loss plus more on accessories, and other software BS.

My advice is to take an Ubuntu LiveCD to CC and try a few models if they will let you.

---

