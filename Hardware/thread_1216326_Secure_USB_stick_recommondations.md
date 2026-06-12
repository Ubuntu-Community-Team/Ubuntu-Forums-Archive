---
title: "Secure USB stick recommondations?"
date: 2009-07-18
forum: Hardware
---

### Post by tp42 on 2009-07-18
Hi there,

I am looking for a secure USB stick, which allows me to securely transport  from Linux/Ubuntu/SUSE to Windows XP/Vista or MacOS X platforms and visa versa. Typically my situation when I should give a talk, getting to the presentation laptop, plugin my USB stick and start the presentation without any hassles.

So, up to my knowledge TrueCrypt and other software in that field are not suitable for my situation, due to the fact that they need admin passwords, or even TrueCrypt installed on the particular platform. This is normally out of scope in these situations.

So, I tried to google for a secure USB stick fitting my needs and found at best a review in Computerworld: [ www.computerworld.com/s/article/print/9062527/Review_7_secure_USB_drives]("http://www.computerworld.com/s/article/print/9062527/Review_7_secure_USB_drives")
However, the article is now older than year, so I would like to ask, if someone wants to share his/her "every day experiences" on Linux/Ubuntu especially with:
[LIST]
[*]The Imation Pivot Plus Flash Drive	
[*]The IronKey Secure Flash Drive
[/LIST]
or any other secure USB stick?

I suppose that MacOS X and Windows XP/Vista compatibility are not a problem.

Thanks in advance,
tp42

---

### Post by SuperSonic4 on 2009-07-18
Any reason why you need an encrypted memory stick? I can understand if your employer(s) want to have it encrypted but as is you shouldn't need encryption on that. Keeping it on your person at all times is much more secure than any encryption

---

### Post by tp42 on 2009-07-18
Hi Supersonic4,
thanks for your comment.
> **SuperSonic4 said:**
> Any reason why you need an encrypted memory stick? I can understand if your employer(s) want to have it encrypted but as is you shouldn't need encryption on that. Keeping it on your person at all times is much more secure than any encryption
In general you are right, although, there are some human factors:
Loosing the stick is one and another is the stick getting stolen by someone just looking for an USB stick.

So I would be really happy to have the data secured on an USB stick, not only to make my employer sleeping well ;-)

---

### Post by hansdown on 2009-07-18
Hi tp42.

A-DATA has a secure thumbdrive. I would personally opt for the password-protect feature.

Other info.

[http://www.computerworld.com/s/article/9062527/Review_7_secure_USB_drives](http://www.computerworld.com/s/article/9062527/Review_7_secure_USB_drives)

---

### Post by tp42 on 2009-07-19
Hi hansdown,
thanks for the tip. I did not know this secure USB stick. It seems an interesting offer. Do you have personal experiences with that secure flash drive (fingerprint reader or password protection feature)?

[QUOTE=hansdown;7635829]

A-DATA has a secure thumbdrive. I would personally opt for the password-protect feature.

---

### Post by hansdown on 2009-07-19
> **tp42 said:**
> Hi hansdown,
thanks for the tip. I did not know this secure USB stick. It seems an interesting offer. Do you have personal experiences with that secure flash drive (fingerprint reader or password protection feature)?

[QUOTE=hansdown;7635829]

A-DATA has a secure thumbdrive. I would personally opt for the password-protect feature.

I only have experience with the SD card. I use it for my camera, and it writes to the card great.

If I plug the card into any computer, it is unreadable. With the usb card reader that comes with it, the card can be read on any computer.

[http://www.adata-group.com/EN/product_show.php?ProductNo=ASDH150BUC](http://www.adata-group.com/EN/product_show.php?ProductNo=ASDH150BUC)


It's not true encription, but rather, it is hardwired to not be readable without the card reader.

The label can be removed, so it looks like any SD card.

If you lose possession of it, most people would think the card is bad.

---

### Post by dess on 2010-05-28
Unfortunately, "A-DATA MyFlash FP1" (and, very likely, "Transcend JetFlash 210" at least) is not protected at all (very bad engineering of chip chosen for device), see for details: [http://nshmyrev.narod.ru/myflash/adata-myflash-fp1.html](http://nshmyrev.narod.ru/myflash/adata-myflash-fp1.html)

For hardware-only solution, looks good "Corsair PadLock" (tested) and "Corsair PadLock 2" especially (not tested yet, but hardware AES-256 encryption implemented).

---

### Post by hansdown on 2010-05-28
> **dess said:**
> Unfortunately, "A-DATA MyFlash FP1" (and, very likely, "Transcend JetFlash 210" at least) is not protected at all (very bad engineering of chip chosen for device), see for details: [http://nshmyrev.narod.ru/myflash/adata-myflash-fp1.html](http://nshmyrev.narod.ru/myflash/adata-myflash-fp1.html)

For hardware-only solution, looks good "Corsair PadLock" (tested) and "Corsair PadLock 2" especially (not tested yet, but hardware AES-256 encryption implemented).

Nice find dess.

I'll bet you can't do that with the SD card.

---

### Post by dess on 2010-05-29
> **hansdown said:**
> I'll bet you can't do that with the SD card.
For classic SD card hardware-based solution is impossible (just DRM features, which AFAIK include encryption, but their implementation looks silly, since there's "security via obscurity" is used and specifications supplied only to license holders, more: [http://en.wikipedia.org/wiki/Secure_Digital#DRM_features](http://en.wikipedia.org/wiki/Secure_Digital#DRM_features)).

But, as SD interface is already in fact much more than just original flash memory device (i. e. there is wireless controllers with SD interface, etc.), there some solution possible. Nothing exactly secured found for the moment, but this project is close in some way:

Eye-Fi card (Google sent them as gift for Picasa subscribers): [http://www.eye.fi/](http://www.eye.fi/)

---

