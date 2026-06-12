---
title: "linux supported wifi cards"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by dphipps on 2005-07-17
I plan to buy a wireless card for my laptop.  Does anyone have any sugestions as to what might be a good card for me to get?

---

### Post by dickohead on 2005-07-17
[QUOTE=dphipps]I plan to buy a wireless card for my laptop.  Does anyone have any sugestions as to what might be a good card for me to get?[/QUOTE]
 Not a NetComm one!!! I haven't been able to get it working with NDiswrapper, open-source drivers or any drivers from the company. They said they do not support Linux, and gave me a link to a web page I *might* find useful... I didn't, as the drivers on the page supplied were not for the card, but I did try them anyway, but to no avail.

I have read promising things about Linksys and D-Link, aswell as Netgear, so I think my next card will be a Linksys, and i'll sell my Netcomm to a Windows user... or maybe a swap is in order?

---

### Post by varunus on 2005-07-17
Find one with an Atheros AR5212 chipset.  The madwifi atheros driver works very well, and is included with Ubuntu (no setup required).

---

### Post by byen on 2005-07-17
stay away from Broadcom .... they say they have no immediate plans to release drivers for linux. Can be configured but why go through the hassle while you have better/compatible ones!

---

### Post by s_p_a_r_k_y on 2005-07-18
Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

thats form my lspci. It works great, and used the "prism54" kernel module, never had a problem with it.

---

### Post by jobli on 2005-07-18
Hi !
I searched linuxquestions.org hardware database and found this card to be working great with the prism driver:3Com OfficeConnect Wireless 11g PC card 3CRWE154G72.
WARNING!!! I bought it and it did not work!!!! ](*,) 
Just want to let you know that this card has been released in a version 2 that won't
work with the prism drivers. I finally got it to work with a driver from linuxant. (Using win drivers.) :mad:

---

### Post by GeneralZod on 2005-07-18
**VAST** amount of info here:

[http://linux-wless.passys.nl/linux_wless.html](http://linux-wless.passys.nl/linux_wless.html)

---

