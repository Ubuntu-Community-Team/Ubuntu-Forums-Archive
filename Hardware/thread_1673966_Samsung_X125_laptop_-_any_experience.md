---
title: "Samsung X125 laptop - any experience?"
date: 2011-01-23
forum: Hardware
---

### Post by hankwang on 2011-01-23
I'm considering to buy a Samsung X125 (More precisely, NP-X125-JA02) laptop. I have not been able to find either positive or negative reports regarding running Linux. Does anyone have experience with it? It's not listed in the (in)compatibility topics in this forum.

Over the years, I've (tried to) run Linux on about 7 laptops and with the exception of the IBM Thinkpad T23 (my first Ubuntu experience!), all of them had some issues with wireless networking, suspend/resume, X11 drivers, sound, and/or web cam. That was even the case with the first Asus Eee and Lenovo Ideapad S10e that came with some pre-installed linux variant.

---

### Post by ajgreeny on 2011-01-23
As always it's very difficult to find out the complete details of what is inside that machine, particularly the wireless chip and the graphic card, though the latter appears to be an AMD/ATI.

Do you have any more detailed specs than this?

---

### Post by hankwang on 2011-01-23
> **ajgreeny said:**
> Do you have any more detailed specs than this?
I found some (Windows) driver downloads and some other data, from various websites.

Video: Internal_VGA_AMD_WXP_8.713.3.0000; ATI Radeon HD4200
Broadcom Bluetooth Driver 5.6.0.5000
Camera Driver 5.66.3700.12
Atheros Wireless Driver 7.7.0.466
Broadcom Wireless LAN Driver 5.60.350.9
Sound(Audio) Driver 5.10.0.6113

The fact that two different makes of wireless drivers are offered makes me worry.

Anyway, how would I figure out from the driver names what chipset is in the laptop? I suppose that a generic Atheros driver supports all Atheros chipsets to date.

---

### Post by hankwang on 2011-01-23
By the way: can one predict whether a laptop may have trouble doing a reliable suspend/wake-up? That shouldn't have a lot to do with the chipset, isn't it?

---

### Post by ajgreeny on 2011-01-23
Some broadcom wireless chips can be a problem, but are often overcome with a bit of work, many atheros chips are fine.

The webcam and sound info that you show does not help as it gives no indication of the hardware installed.

As for suspend and hibernate, that very often is a bit of a suck it and see business, so it is difficult to give more help to you, unless you can find other users who can say more.

---

### Post by putte123 on 2011-02-01
I have a Samsung X125 with Ubuntu 10.10 running on it. It works perfect. All HW works out of the box except the WLAN chipset. Mine has a broadcom WLAN chipset it works with the broadcom sta driver. Ubuntu will ask if this driver shall be install.

Overall I'm vary happy with this laptop.

---

