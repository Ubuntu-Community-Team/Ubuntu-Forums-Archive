---
title: "ASUS 1005HA wireless networking stopped working"
date: 2010-07-25
forum: Hardware
---

### Post by eccentric on 2010-07-25
Hi,

I've been using Lucid since June on my ASUS 1005HA with wireless working okay until yesterday. Now for some reason the wireless will successfully connect to the router but it is not able to resolve any domain names (e.g., when I try to ping Google I get an "unknown host www.google.com" error).

I'm showing about 70% connection strength. I'm able to successfully connect to the same router and browse the Internet when I boot into Windows 7 on the same netbook. I'm also able to connect and browse using my Windows 7 desktop in the same room. I've tried installing the wireless module backports but those don't seem to be helping.

Sometimes I'll be able to successfully ping Google and browse the Internet but that only happens about once every five times I try.

Thanks for any help you can provide!

---

### Post by eccentric on 2010-07-26
Fixed by installing ndiswrapper (instructions here [http://www.wluopensource.org/articles/view/setting-ndiswrapper-ubuntu-lucid-lynx/]("http://www.wluopensource.org/articles/view/setting-ndiswrapper-ubuntu-lucid-lynx/"))

---

### Post by soilland on 2010-09-11
Thank you so much.

---

