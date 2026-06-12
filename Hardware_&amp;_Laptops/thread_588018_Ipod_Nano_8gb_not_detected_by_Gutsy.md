---
title: "Ipod Nano 8gb not detected by Gutsy"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by canesalato on 2007-10-23
Hello, I've just installed ubuntu 7.10 and I have a problem with Ipod nano 8gb.
If I plug it nothing happens at all!
- I do not get the "do not disconnect message" on the ipod display
- nothing appears in the desktop!
- " dmesg | grep iPod " returns nothing! :(
So it's simply as the system doesn't detect the ipod at all!!
I don't know where to start with this :(

---

### Post by russnash37 on 2007-10-23
Can I take it that your ipod was detected on a previous version of Ubuntu or other Linux distribution?

Connect your ipod to the computer, wait about one minute then paste the output here from the following two commands:

     dmesg | grep "usb"

     dmesg | grep "sd"

From there, we should (hopefully) be able to ascertain what is going on.

Russ.

---

### Post by tgalati4 on 2007-10-23
What devices are listed under:

>ls -la /media

---

