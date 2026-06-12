---
title: "Newbie trying to get modem to work"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by dbouthillier on 2005-02-21
I have just installed ubuntu on my desktop which is a dual with Windows. I would like to get my dial-up modem working so I can access the Internet.

I know very little about Linux and very little about configuring hardware devices. I remember in Windows having to go into the Control Panel and adding 'New Hardware' when I first installed in order for my modem to work. As far as I know, I do not have a disc with any drivers for it.

I looked in the Windows Device Manager for the maker of the modem, which is 'HSP56 MicroModem by PCtel'. 

If anyone knows how to get my modem working for ubunto Linux, that would great!!

---

### Post by az on 2005-02-22
'HSP56 MicroModem by PCtel'

That is a software modem (winmodem).  It is based on the pctel chipset.  The pctel people have yet to make linux driver that works with the linux 2.6 kernel.

Take a look at winmodems.org

You should complain to the manufacturer.

---

### Post by dbouthillier on 2005-02-22
So are you saying that my modem will not work with Linux? What should I do? I tried to look at the winmodems.org website but I couldn't find it.  :-?

---

### Post by m4ng0 on 2005-02-22
[QUOTE=dbouthillier]
...
I tried to look at the winmodems.org website but I couldn't find it.  :-?[/QUOTE]

[www.linmodems.org](http://www.linmodems.org)

---

### Post by Chrissie on 2005-08-07
[http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html) has a new driver for kernel 2.6.

Hope this helps.
Christel

---

