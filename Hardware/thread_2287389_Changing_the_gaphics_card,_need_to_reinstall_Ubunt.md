---
title: "Changing the gaphics card, need to reinstall Ubuntu?"
date: 2015-07-19
forum: Hardware
---

### Post by whitefish10 on 2015-07-19
Hi guys, I want to make sure if I need to reinstall Ubuntu 15.04 if I want to upgrade the graphics card. I am sure it is not, but I need someone to confirm.

Note in Ubuntu I selected the property driver for this card from AMD (option property-updated) if am not reinstalling Ubuntu, should I just restore it to the open source driver before changing the card?

Thanks in advance.

---

### Post by sudodus on 2015-07-19
Yes, it is a good idea to restore the system to use the open source graphics driver (by removing the proprietary graphics driver). After you have installed the new graphics card, maybe you want or need to install a proprietary driver again.

---

### Post by Bucky Ball on 2015-07-19
Personally, I would go to the Additional Drivers and switch the AMD driver off it is in there. Shut the machine down, install the new card, boot up and see what happens. It should select the appropriate driver for you card, which will probably be the open source one.

There should be no reason to reinstall the OS.

---

