---
title: "IBM T40: the sound doesn't work."
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by tazdzioch on 2007-09-22
Hi!

My intel sound card worked well on kubuntu 6.10.

After my upgrade on kubuntu 7.04, it stopped working.

> xxxx@xxxx:~$ lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
xxxx@txxxx:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: I82801DBICH4 [Intel 82801DB-ICH4], urz&#261;dzenie 0: Intel ICH [Intel 82801DB-ICH4]
Urz&#261;dzenia podrz&#281;dne: 0/1
Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: I82801DBICH4 [Intel 82801DB-ICH4], urz&#261;dzenie 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
Urz&#261;dzenia podrz&#281;dne: 1/1
Urz&#261;dzenie podrz&#281;dne #0: subdevice #0


Then I rebooted the computer (it apparently is a known bug):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893")

But still it doesn't work.

Thanks for any kind of help!

---

