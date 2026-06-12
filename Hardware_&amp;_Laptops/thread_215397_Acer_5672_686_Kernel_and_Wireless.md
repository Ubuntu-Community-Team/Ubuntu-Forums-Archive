---
title: "Acer 5672 686 Kernel and Wireless"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by oobnuker on 2006-07-13
I got 6.06 installed on my 5672 and everything seemed to work OK with the 386 kernel, but when I switched to the 686 kernel, I no longer have wireless. The WiFi adapter is not even recognized anymore.

I'm sure this has been hashed out already, but I can't seem to find it in the 5672 thread (45 pages...).

Anyone got the answer to this? 

Thanks.

---

### Post by ltmon on 2006-07-14
I have the same problem.  Another thread said to install the restricted modules for 686, but this doesn't seem to help me.

I'm using the SMP version of the 686 kernel.

L.

---

### Post by oobnuker on 2006-07-14
I already have the restricted modules loaded. I went ahead and reinstalled them and that did not appear to help either. I am also using the SMP kernel (didn't mention that in the original post).

---

### Post by ltmon on 2006-07-14
I fixed it.

After the installation of the 686 SMP kernel there were two versions installed: 2.6.15.23 and 2.6.15.26.

But the restricted modules only existed for 2.6.15.23.  So select this option from Grub and start up.  You should be able to edit /boot/grub/menu.lst to make this the default.

It seems like this is a packaging error or simply someone didn't get around to releasing the restricted modules for the latest version.

L.

---

### Post by oobnuker on 2006-07-15
You hit it! Thanks - I knew it would be simple.

---

### Post by dandy411 on 2006-07-20
I have an acer 5672 been working with latest version of ubuntu . I can see networks wifi acts like its there but when I try to connect it flashes like mad says connected takes 4 ever . Then I disconnect my ethernet and ....U guessed it ...the same problem every 1 else is having :( I have 2 wireless networks 1 wep encrypted the other wpa2 . It sees both just wont join . I just did a clean install then updated with the latetest patches. I need HELP getting my wifi and orbi cam working .Any suggestions?

---

### Post by dandy411 on 2006-07-20
I found the official support for the wifi driver from intel at this link [http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=2259&dwnldid=10315&agr=y&lang=eng&prdmap=2259](http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=2259&dwnldid=10315&agr=y&lang=eng&prdmap=2259)


Still unable to get it up in runing :(

---

