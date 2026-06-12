---
title: "wireless pendrive ASUS WL-167G do not connect"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by sharemind on 2008-04-13
Hello,

I am new to linux. I have just installed ubunto 7.04 on my PC, but I am not able to connect to internet using a wireless USB pendrive ASUS WL-167G :confused:

Is there someone that can give me a hand??

Thanks a lot in advance

---

### Post by zeronio on 2008-04-21
I have the same problem. I will try what is suggested here:

[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)

---

### Post by sharemind on 2008-04-21
I have already try to use **ndiswrapper**

but for me did not work. 

Let us know if you succeded :)

I will try with **ubuntu version 8** that is coming out in few days.... it may have more hardware compatibility!

---

### Post by zeronio on 2008-04-22
No - it didn't work. The problem was similar as with rt2500usb module. The network was listed but I couldn't connect to it.

Then I tried release candidate of Ubuntu 8.06 and it works!
But... still not very stable. Every once and a while it looses connection and I have to reconnect or even unplug/plug it again.

I found the sources linux driver rt2500usb on the Asus page, so they wrote or sponsored it, but they didn't do a very good job IMHO.

---

