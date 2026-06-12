---
title: "Pcmcia wireless card not activated on computer restart"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by firecat53 on 2005-08-21
Hey.  The PCMCIA wireless card (Dlink dwl-g630) in my Dell Inspiron 7000 normally works fine, but when I restart the computer it doesn't get activated.  Dmesg gives the following error:

cs: pcmcia_socket1: voltage interrogation timed out.

Any thoughts?

thanks, Scott

---

### Post by evilghost on 2005-08-21
[http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001818.html](http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001818.html)
[http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001819.html](http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001819.html)

---

### Post by firecat53 on 2005-08-21
Thanks for the response...I've got the identical problem that he described in the link you posted. However, I'm a little hesitant to apply the patch because 1. It didn't work for the other person that tried it and 2. It sounds like the problem the patch was designed for was getting an error on inserting the card rather than on a reboot.  The card works fine on initial boot, if it is removed and then reinserted and waking up from a suspend. It's only when the computer is rebooted that there's an issue. 

Could there just be an issue with the card not being shut down properly?

Thanks, Scott

---

