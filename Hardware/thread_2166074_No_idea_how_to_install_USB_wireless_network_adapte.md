---
title: "No idea how to install USB wireless network adapter?"
date: 2013-08-07
forum: Hardware
---

### Post by StrictlyStupid on 2013-08-07
Hey everyone. I recently purchased a new wireless network adapter(Edimax EW-7811Un) to replace the broken wifi antenna in my laptop. It came with a CD that had the drivers I needed on it.  Problem is, being a relatively new Linux user, I have absolutely no idea how to actually install the drivers and get this thing working. Here's a screenshot of the "linux driver" folder from the cd: [http://imgur.com/JrgEe3u.png](http://imgur.com/JrgEe3u.png)

I hope it's not asking too much, but could anyone fill me in on how to install this kind of driver?

---

### Post by kurt18947 on 2013-08-07
I have that adapter and it works very well.  I used the driver from RealTek on 12.04, 12.10 and variants.  RealTek's driver failed with 13.04 & later.  There was some work done by those more knowledgeable than I and their solution works well.  Here's a thread that details experiences of myself and others:

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs) 

Tim Phillips' .deb file can be found here:

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

The .deb file not only enables the adapter on newer releases, it also adds DKMS functionality so kernel updates don't break the driver.

---

