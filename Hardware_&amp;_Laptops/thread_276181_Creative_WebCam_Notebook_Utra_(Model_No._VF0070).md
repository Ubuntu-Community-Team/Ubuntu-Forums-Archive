---
title: "Creative WebCam Notebook Utra (Model No. VF0070)"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by Meck1982 on 2006-10-12
Hi everybody,

is there anybody out there having experiences with the Creative WebCam Notebook Utra (Model No. VF0070) running in Ubuntu?
I tried some drivers on [http://mxhaard.free.fr/spca50x/Download/]("http://mxhaard.free.fr/spca50x/Download/") but without success. Perhaps I am doing anything wrong with compiling or installation.

Whould be very nice if somebody having this working could post a lil howto.

---

### Post by mjukis on 2007-03-13
Did you ever got this to work?

I have the same webcam and I cant get it to work. I have tried the gscpa drivers with no luck.

Here are som more info about the webcam if it helps.

Vendor=041e ProdID=403d Rev= 1.00
Manufacturer=SQ Tech CO., LTD.
Product=USB 2.0 PC camera

---

### Post by jackrobinson on 2007-03-13
> **Meck1982 said:**
> Hi everybody,

is there anybody out there having experiences with the Creative WebCam Notebook Utra (Model No. VF0070) running in Ubuntu?
I tried some drivers on [http://mxhaard.free.fr/spca50x/Download/]("http://mxhaard.free.fr/spca50x/Download/") but without success. Perhaps I am doing anything wrong with compiling or installation.

Whould be very nice if somebody having this working could post a lil howto.

Automatix2 installs the spca5xx drivers correctly. Have you given that a shot?

---

### Post by mjukis on 2007-03-14
spca5xx is for older kernels and gscpa is the same(?) but for newer kernels if I understood correctly from the site [http://mxhaard.free.fr](http://mxhaard.free.fr).

Anyhow this specific camera is not supported by this driver. I am trying to change the sourcecode for the gspca drivers and adding my own webcam but I'm not a skilled programmer so I don't know if I'll ever suceed. 

I'm running Kubuntu (Fiesty) with kernel 2.6.20-10 right now so I can't compile spca5xx since it require a .c-file that is no longer included in the kernel source.

---

### Post by mjukis on 2007-04-05
I didn't get it to work. Hopfully there are some other linux user with the same webcam model who might help. Here is a [link to the manufacturers homepage]("http://us.creative.com/products/product.asp?category=218&subcategory=553&product=11491&nav=technicalSpecifications"). Hopfully it will help.

---

### Post by knockout on 2007-04-13
I own this webcam too, and I believe the only person who is working towards a possible driver in Linux is Gerard Klaver. His status page is at [http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html)

Recently, he has been able to capture RAW images from the webcam. I don't know if it can be made v4l compatible any time soon.

---

