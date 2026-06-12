---
title: "Acer 5613Z WLMI"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by BoBoL on 2007-06-13
Hello all,

I'm a happy Ubuntu user :p since 3 years, but now... i've a(some) problem(s) i can't resolve alone so i'll ask for your experience an so your help please.

I've an Acer 5613Z WLMI laptop, and i really like it but i've got 2 big problems on it.

The first one:
My wifi card -  05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01) - Atheros AR5007EG
I've tried to compile the lastest drivers, no results...
I've tried ndiswrapper, it hangs my pc and doesn't work too...

The second and last one:
My integrated webcam - this is it's id "5986:0100"
I've tried to compile both the lastest uvcvideo & gscpa, no results too... snif

As anyone any idea of how to resole my problems or is it simply because my material is not yet comptaible with those drivers???

Thanks!!!

It forgot, sorry for my poor english...

---

### Post by BoBoL on 2007-06-15
Just an up!!!

---

### Post by ugm6hr on 2007-06-15
Really don't know, but thought I'd point you to this:

#
Laptop: Acer Aspire 5570Z

    *
      Chipset: Atheros AR5007EG (rev 01)
    *
      PCI ID: 168c:001c
    *
      Driver: [ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip)
    *
      ndiswraper version : > 1.45
    *
      other : need to uninstall all madwifi kernel module before use ndiswrapper
    *
      other : if you can’t get any AP signal, try to enable wifi radio through wlan switch (it’s look like nothing happened when you try to enable through wifi, because the LED is not compatible with linux(i’m using ubuntu 7.04), but if you try ‘iwlist wlan0 scan’ you’ll see some AP information

(from ndiswrapper wiki)

Seems to suggest that  this chipset should work with ndiswrapper, but only if you have version >1.45 (which means you will have to compile it from source) and you uninstall the madwifi module.

Unfortunately, I have no idea how to do either of these things...

---

### Post by BoBoL on 2007-06-16
Thanks, i'll try it a soon as possible and i'll tell you if it worked!!!

EDIT: Thanks a lot, so i don't have madwifi drivers working but ndiswrapper works now!!! I just did not have the good drivers at the first time!!! LoL!!!

---

### Post by ugm6hr on 2007-06-16
Glad that helped... Have to say, I probably wouldn't have been able to make it work myself ;)

---

### Post by Anjue on 2007-06-16
I have The same Problem about webcam too. How can I find the id?

---

### Post by BoBoL on 2007-06-16
It's not very difficult to do it with ndiswrapper, of course you shouldn't be idiot like me and download the wrong drivers...

If you want to have the id of the webcam just type "lspci".

---

### Post by capiscuas on 2007-07-04
[Here]("http://ivangarcia.org/blog/?p=13") there is a post about how to install Ubuntu with a laptop with that WIFI Atheros card.

---

### Post by capiscuas on 2007-07-24
> **BoBoL said:**
> Hello all,

I'm a happy Ubuntu user :p since 3 years, but now... i've a(some) problem(s) i can't resolve alone so i'll ask for your experience an so your help please.

I've an Acer 5613Z WLMI laptop, and i really like it but i've got 2 big problems on it.

The first one:
My wifi card -  05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01) - Atheros AR5007EG
I've tried to compile the lastest drivers, no results...
I've tried ndiswrapper, it hangs my pc and doesn't work too...

The second and last one:
My integrated webcam - this is it's id "5986:0100"
I've tried to compile both the lastest uvcvideo & gscpa, no results too... snif

As anyone any idea of how to resole my problems or is it simply because my material is not yet comptaible with those drivers???

Thanks!!!

It forgot, sorry for my poor english...

[Here]("http://ivangarcia.org/blog/?p=13") is how I did to make the 5986:0100 webcam work with KOPETE.:popcorn:

---

