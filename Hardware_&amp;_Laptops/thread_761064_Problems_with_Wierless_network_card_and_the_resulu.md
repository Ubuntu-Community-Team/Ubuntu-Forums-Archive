---
title: "Problems with Wierless network card and the resulution"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by flyturkish on 2008-04-20
Hello I installed Ubuntu 8.04 using Wubi witch works quiet well on my Fujitsu Siemens laptop for the first time ever I have never used Linux before so I am quiet new to Linux I really like it but I have some problems 

First Some hardware is not recognized I can not connect to the Internet I only have access to a wireless network, I can only choose from Dial up and Ethernet but my Wireless adaptor card what ever is in my laptop dose not show up !. 

Also the resolution is pretty  high 800 x 600 .

It would be so cool if some one of you could help me to sort out my problem with the wireless network card and the resolution.  

thanks flyturkish

---

### Post by Gen2ly on 2008-04-20
just so you know resolution can be changed by editing xorg.conf.  I'm not sure how Wubi works but looking for the line in /etc/X11/xorg.conf with 800x600 and editing it will fix it.  there are many guides out there to help new users including ubuntu's documentation which is pretty good.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://wiki.ubuntu.com/DocumentationTeam/GettingStarted?action=fullsearch&context=180&value=getting+started&titlesearch=Titles](https://wiki.ubuntu.com/DocumentationTeam/GettingStarted?action=fullsearch&context=180&value=getting+started&titlesearch=Titles)

---

### Post by flyturkish on 2008-04-20
Thank you I will try to get my resolution fixed . I had a look in the Hardware Drivers application and it says
that some of the hard ware is not supported due to the fact that information about them where not given by the manufacturer , I says the following


Atheros hardware access layer (HAL) 

and the

Atheros 802.11 wireless lan cards  

are not supported they are enabled I am not really sure how to get those up and running ? 

if some one has some advise for me I would appreciated

thanks flyturkish

---

