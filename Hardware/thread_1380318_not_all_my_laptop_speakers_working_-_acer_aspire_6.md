---
title: "not all my laptop speakers working - acer aspire 6530"
date: 2010-01-13
forum: Hardware
---

### Post by dazift on 2010-01-13
I have an acer aspire 6530 with "tuba" bass speaker built in that i cannot get to work under ubuntu. I am running 9.10 and I had the same problem with 9.04 and never fixed it. I tried [this]("http://monespaceperso.org/blog-en/2009/04/29/acer-aspire-6920-bass-not-working-on-ubuntu-jaunty-904/") with no change. 

```
@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
```

I'm not very familiar with how sound works in ubuntu, but if someone can fill me in on settings that I can play around with that I dont know about it would be appreciated, Thanks.

I also have a dual boot with Vista. When I boot Vista a few times and shutdown and boot into ubuntu, the tuba works for one startup. if I log out or reboot into ubuntu, it stops working again.

---

