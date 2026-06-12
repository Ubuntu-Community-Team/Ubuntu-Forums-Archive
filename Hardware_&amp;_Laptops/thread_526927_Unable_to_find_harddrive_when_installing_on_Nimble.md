---
title: "Unable to find harddrive when installing on Nimble V5"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by wrc4 on 2007-08-16
Hi, this is my FIRST post on ubuntuforum.

I'm trying to install Ubuntu 7.04 on my "Nimble V5" PC [http://www.bigbruin.com/html/nimblev5.htm]("http://www.bigbruin.com/html/nimblev5.htm").

I tried Ubuntu 6.10 and 7.04 Desktop CD and Xbuntu 7.04 alt CD. None of them could find the internal hitachi 80G 2.5" harddrive during installation. I was asked to choose a driver from a list but I tried all of them (including via82cxxx) without success.

For comparison I installed Fedora Core 7 on it. FC7 was able to recognize the harddrive. I checked the driver it used, it is called: pata_via.ko. So I copied that module to /lib/modules... and did a insmod, but insmod returned an error.

Can anybody give me some help on this? I would really like to use Ubuntu or Xubuntu on my V5.

---

### Post by dougfractal on 2007-08-16
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72888](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72888)
> Yes, pata_via is missing because it breaks things.

---

### Post by wrc4 on 2007-08-16
OK. But somehow Fedora Core 7 works well. Do you mean if I use a newer kernel pata_via.ko will work? If that's the case how can I install Ubuntu using the desktop or alt CD?

---

### Post by dougfractal on 2007-08-17
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72888](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72888)

> linux-image-2.6.20-2-generic + pata_via is working well

> pata_via.ko is missing on linux-image-2.6.20-6-generic.

> via82cxxx.ko was included in 2.6.17 package (from Edgy Eft).
You will need to custom kernel, install with Edgy Eft

---

