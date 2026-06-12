---
title: "No Network Detected"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by lvargas on 2005-07-13
After the installation of ubuntu, when i started up my pc, Ubuntu no detected any of my Network cards.

I've wrote:

[COLOR=Green]lspci[/COLOR]

So my network cards are:

[B]0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10) 

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)[/B]

Then I've worte:

[COLOR=Green]luis@MY-PC:-$ sudo modprobe 8139[/COLOR] 4 Realtek

then i saw the following message:

sudo: unable to lookup Satellite-A10 via gethostname() 
Password: postdrop: warning: unable to look up public/pickup: No such file or directory

Then, I've logged as a root, the following message appeared:

sudo: unable to lookup Satellite-A10 via gethostname() 
Password: postdrop: warning: unable to look up public/pickup: No such file or directory 
FATAL: Module 8139 not found

How can i get, that my network cards be recognized???  ](*,)

---

### Post by stepper on 2005-07-14
[QUOTE=lvargas]Then I've worte:

[COLOR=Green]luis@MY-PC:-$ sudo modprobe 8139[/COLOR] 4 Realtek

then i saw the following message:

FATAL: Module 8139 not found

How can i get, that my network cards be recognized???  ](*,)[/QUOTE]
I think it should be modprobe 8139cp or 8139too

---

