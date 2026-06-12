---
title: "Don't recognize pcmcia"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by LinxNew on 2005-05-16
Hi,

I've had some big problem to install Ubuntu, because at hardware detect, it's block at pcmcia. 
So after some test, I must disable to auto-detect at installation, and now I can use my fantastic Hoary.
But now I would like to configure my pcmcia: I have a toshiba.

Hoary cannot recognize my IEEE 1394 Host Controller.

And yes, I have the same problem of other topic: don't recognize my 6 in 1 card reader.

if I use command :

modprobe slamr
/usr/sbin/slmodemd --country=xxxx  /dev/slamr0
(as root)

why I have an error for 'slamr' ?


Thank you for all your support.

---

### Post by az on 2005-05-16
Is pcmcia_cs installed and where did you get the modem drivers?

---

### Post by LinxNew on 2005-05-23
Hi, 

excuse for delay. I've reinstalled Hoary.

I've installed modem from ubuntuguide, but doesn't recognize yet.

---

