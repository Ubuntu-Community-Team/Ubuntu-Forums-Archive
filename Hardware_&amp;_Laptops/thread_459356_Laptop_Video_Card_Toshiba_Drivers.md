---
title: "Laptop Video Card Toshiba Drivers"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-05-30
Hello all, I am thinking of getting this laptop:

[http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=368658&seg=HHO](http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=368658&seg=HHO)

CC has a great price on it.

It has an Atheros wireless card.  I know this as I went to CC and in the Vista device manager it said Atheros 5006EG.  Feisty supports that out of the box.  I want to wipe the drive and install Feisty when I get it.

What about the chipset and video card?  It has an Intel Media accelerator 950 for the video card.

Does Ubuntu support this card for having 3D acceleration?  I want to use Google Earth and that requires OpenGL.

Thanks

---

### Post by stchman on 2007-05-30
After a bit of reading would this do it?

sudo apt-get install xserver-xorg-video-intel

Does this install true opengl or MESA?

Thanks

---

### Post by stchman on 2007-05-30
Anyone?

---

### Post by mattmyers83 on 2007-05-30
Just to give you a heads up this laptop and most Toshiba laptops use a intel ac97 codec sound driver.  This specific models chipset is an el cheapo realtek id85 which is flakey at best in Feisty.

---

### Post by stchman on 2007-05-30
> **mattmyers83 said:**
> Just to give you a heads up this laptop and most Toshiba laptops use a intel ac97 codec sound driver.  This specific models chipset is an el cheapo realtek id85 which is flakey at best in Feisty.

I have a A135-S2246 Toshiba laptop and everything works well.  It has an ATI Radeon Xpress 200M video card and an SB450 sound card that work well under Feisty.

I would just like to know if Feisty supports the GMA 950 for 3D acceleration.

The laptop I want uses an 845GM chipset, Atheros wireless, and GMA 950 for graphics.

---

