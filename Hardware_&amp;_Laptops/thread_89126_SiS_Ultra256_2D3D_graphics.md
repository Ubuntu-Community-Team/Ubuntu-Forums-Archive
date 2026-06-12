---
title: "SiS Ultra256 2D/3D graphics"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by ThirdWorld on 2005-11-11
Hi everyone, i am really considering to buy a new laptop. i found this at walmart which i think is really cool and affordable. [http://www.walmart.com/catalog/product.do?product_id=4025846]("http://www.walmart.com/catalog/product.do?product_id=4025846")

my question is, do you guys have any experience with this laptop\graphic chipset? do you guys think it will work with Breezy? I cant find any reference in the forums about it. Thanks :)

---

### Post by gmc on 2005-11-12
Looks pretty interesting. Though two things jump out at me.

1. At 7 pounds, hope you don't plan on toting it around too much.
2. I didn't see any mention if the video ram was shared or not. I suspect it is on this
    model. So 256M may not be what is left for the OS/APPS. 

    Also, I do recall reading somewhere that SIS video chipsets aren't well supported, but for the life of me, I can't find the source.

Hope this helps, the price is certainly right.

G.

---

### Post by ThirdWorld on 2005-11-12
thanks for the reply, actually in this laptop the ram is shared with the graphic chip, but the system ram its upgradable to 1 GB. Somebody told me that in theory you can designate 128mb to the video chip and you still have 872mb available for your applications. Also, this chip is 256bits  wich i think is not bad, but what im affraid is that Ubuntu will not support the chips share memory architecture...
I dont want to run other thing that linux in my new laptop, i hate windows xp...

Any suggestions enyone?...

---

### Post by ubuntu_123 on 2005-11-13
You may want to read this:

[http://www.winischhofer.at/linuxsispart4.shtml#download](http://www.winischhofer.at/linuxsispart4.shtml#download)

At the bottom of the page you can find this if you don't want to read the whole thing:

"And for the last time: There is no DRI/OpenGL (hardware accelerated 3D) support for the SiS 315/65x/74x/330/66x/760/761/340/XGI and I am not aware of any development in that regard. "

I am not sure those are include your chipset or not, but you can explore the whole site or ask question in that forum.

Sis chipset is too much trouble for me, I finally get rid of my Acer wlci3003 with lost a few hundred dollars for only purchased two month.

---

### Post by ThirdWorld on 2005-11-13
[QUOTE=ubuntu_123]You may want to read this:

[http://www.winischhofer.at/linuxsispart4.shtml#download](http://www.winischhofer.at/linuxsispart4.shtml#download)

At the bottom of the page you can find this if you don't want to read the whole thing:

"And for the last time: There is no DRI/OpenGL (hardware accelerated 3D) support for the SiS 315/65x/74x/330/66x/760/761/340/XGI and I am not aware of any development in that regard. "

I am not sure those are include your chipset or not, but you can explore the whole site or ask question in that forum.

Sis chipset is too much trouble for me, I finally get rid of my Acer wlci3003 with lost a few hundred dollars for only purchased two month.[/QUOTE]


WOW that sucks BIG TIME... almost all the low end laptops that you can buy out there come with that graphic chip set....

---

### Post by ThirdWorld on 2005-11-13
[http://www.linux.org/docs/ldp/howto/Hardware-HOWTO/video.html]("http://www.linux.org/docs/ldp/howto/Hardware-HOWTO/video.html")

in this link they said Linux support the SIS graphic chip set...



SiS 3D PRO AGP	SiS6326	XF86_SVGA	sis	 
SiS 530	SiS530	XF86_SVGA	sis	 
SiS 530/620	SiS530	 	sis	 
SiS 540	SiS540	XF86_SVGA	sis	 
SiS 550	 	 	sis	 
SiS 5597	SiS5597	XF86_SVGA	sis	 
SiS 5597/5598	 	 	sis	 
SiS 5598	SIS5598	XF86_SVGA	sis	 
SiS 620	SIS620	XF86_SVGA	sis	 
SiS 630	SiS630	XF86_SVGA	sis	 
SiS 630/730	SiS630	 	sis	 
SiS 6326	SiS6326	XF86_SVGA	sis	 
SiS 650/M650/651/740	SiS650	 	sis	 
SiS 660/661FX/M661FX/M661MX/741/741GX/M741/760/M760	 	 	sis	 
SiS SG86C201	SIS86C201	XF86_SVGA	sis	 
SiS SG86C205	SIS86C205	XF86_SVGA	sis	 
SiS SG86C215	SIS86C215	XF86_SVGA	sis


can somebody help me, Im confused. can I buy a laptop with the SIS chip and install ubuntu on it?? will ubuntu support the video chip? :confused:

---

### Post by gmc on 2005-11-15
Hi,

   I think the answer is Yes. You may not be able to get accelerated graphics working but it (Ubuntu) will work with framebuffer mode. When you are installing Ubuntu, if it can't figure out what chipset to use, it will bring up a list for you to choose from. If you get that list, just select the vesa driver and all should be well (thought it might be a little slow).

Personally I use the vesa driver on my laptop with and NeoMagic chipset and other than not being able to get accellerated graphics on GL based programs, I'm quite happy.

Try booting with the live cd/dvd and see what you get. If it works with that, then it'll work with the installed version too.

G.

---

