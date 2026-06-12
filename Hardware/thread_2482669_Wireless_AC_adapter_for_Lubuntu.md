---
title: "Wireless AC adapter for Lubuntu"
date: 2023-01-07
forum: Hardware
---

### Post by wjbmd48 on 2023-01-07
Hi:

I'm looking for a low-profile (sticks out less than an inch) AC wireless adapter for Lubuntu. I've got a little experience with compiling drivers for the underlying chipsets, but it's cumbersome and really don't want to go through that again.

Looking through the available hardware on Amazon, there are a number that list linux support,  but when you look at the comments and answered questions, the experience with all the ones I've looked at is uniformly miserable "Yes, linux support was advertised, but this turned out not to be true."

Has anyone had any experience with AC wireless adapters that work out of the box with Ubuntu/Lubuntu?

Thanks,

Bill

---

### Post by Autodave on 2023-01-09
Maybe its just me, but what exactly is an AC wireless adapter?

Are you talking about a wifi adapter?  I have an Edimax.....don't remember the model.  Protrudes maybe 1/2" at most.  Works very well.  I did have to install a driver for it, but it was readily available in Synaptic Package Manager.

---

### Post by wjbmd48 on 2023-01-09
Yep, that's what I'm talking about.  When I put Edimax wifi adapter, this is what I see.

Which one to you have? And synaptic/muon really had a driver? Cool.

Let me know,

Thanks,

Bill

---

### Post by wjbmd48 on 2023-01-09
Oops, forgot to post the link:

[https://www.amazon.com/s?k=edimax+usb+wifi+adapter&crid=1UCQZSHTHRNVV&sprefix=edimax+usb+wifi+adapter%2Caps%2C219&ref=nb_sb_noss_1](https://www.amazon.com/s?k=edimax+usb+wifi+adapter&crid=1UCQZSHTHRNVV&sprefix=edimax+usb+wifi+adapter%2Caps%2C219&ref=nb_sb_noss_1)

---

### Post by wjbmd48 on 2023-01-09
Oops, forgot to post the link:

[https://www.amazon.com/s?k=edimax+usb+wifi+adapter&crid=1UCQZSHTHRNVV&sprefix=edimax+usb+wifi+adapter%2Caps%2C219&ref=nb_sb_noss_1](https://www.amazon.com/s?k=edimax+usb+wifi+adapter&crid=1UCQZSHTHRNVV&sprefix=edimax+usb+wifi+adapter%2Caps%2C219&ref=nb_sb_noss_1)

---

### Post by Autodave on 2023-01-10
**[SIZE=4]Edimax Wi-Fi 4 802.11n Adapter is what I have.  The driver was in synaptic, but I do not remember which one.  Sorry.[/SIZE]**

---

### Post by wjbmd48 on 2023-01-10
Thank you!

Bill

---

### Post by wjbmd48 on 2023-01-12
Edimax support is pretty good. The official driver for their low-end wireless-N dongle only worked as high as kernel 4.4.3, and I had 5.15. They eventually pointed me to a github download with good instructions, that I eventually got to work.

---

