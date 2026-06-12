---
title: "acer aspire 1360 modem problem"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by vergispanagiotis on 2005-06-02
hello
i have acer 1360 laptop 
do you know where i can find driver for my modem
agere systems ac'97
please help!!!!!!!!!!!

---

### Post by xristos on 2005-06-03
Geia sou Panagiwti !!!
You can start from here [http://www.ubuntuguide.org/#installsmartlinkdriver](http://www.ubuntuguide.org/#installsmartlinkdriver)

---

### Post by az on 2005-06-03
Agere may also be a lucent modem:

see here:
[http://test.wiki.ubuntu.com/forum/hardware/modem](http://test.wiki.ubuntu.com/forum/hardware/modem)
[http://test.wiki.ubuntu.com/forum/hardware/lucent](http://test.wiki.ubuntu.com/forum/hardware/lucent)
[http://test.wiki.ubuntu.com/forum/hardware/smartlink](http://test.wiki.ubuntu.com/forum/hardware/smartlink)

---

### Post by recmar on 2005-06-03
Hi!
I've got an Aspire 1353 with the same modem. It didn't work with sl-modem-modules and daemon as explained in unofficial Ubuntu guide. I had to install sl-modem from source: [http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.9a.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.9a.tar.gz)
After unpacking take a look in a read file. Installation requires kernel source but you can use kernel headers instead.
Good luck.

---

