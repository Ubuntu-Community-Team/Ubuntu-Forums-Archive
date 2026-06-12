---
title: "Installing a Intel Pro/Wireless 3945"
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by Dan Hinojosa on 2006-04-25
I saw another thread about 3945 and it looked dated.  I download the driver from intel and the ancillary including ieee80211-1.1.13.tgz. I unpacked the ieee package first and ran: make

It failed because it is looking for gcc-3.4.
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found.

I noticed that my unbuntu (I don't know what build I have) comes with only 3.3 and 4.0 gcc. 

How do I get around this.

Any and all help is appreciated.

---

### Post by Dan Hinojosa on 2006-05-07
Anyone?

---

### Post by gmc on 2006-05-09
[QUOTE=Dan Hinojosa]Anyone?[/QUOTE]

Hinojosa,

If you're referring to [this]("http://www.ubuntuforums.org/showthread.php?t=140085&highlight=3945") thread? I can assure you it's very much active and there are detailed instructions on how to compile and install the 3945 driver. However, it sounds like you are using Breezy and unfortunately you'll need to upgrade to Dapper to solve the problem.

Please note that as of Beta2 or Fight7, the 3945 driver is 0.0.74 which doesn't support WPA encryption. You'll need to use 1.0.2 or later to get WPA support. The 0.0.74 driver does work with WEP encryption though.

Gord

---

