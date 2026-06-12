---
title: "&quot;This site can't be reached&quot;"
date: 2017-11-07
forum: Hardware
---

### Post by el canadiano on 2017-11-07
Hey guys,

I recently installed a UEFI instance of Ubuntu MATE (17.10), after previously having a BIOS version of 17.04. Upon the first boot, I recall being able to use Ubuntu just fine. However, more recently, anytime I try to use Chromium, Firefox, or any device that uses the internet, it seems like it is unable to access any website, even though it says that I am both connected to Ethernet and my Wireless Internet as well.

I have not previously had any problems on 17.04.

Is there anything that could be wrong with my 17.10 installation? I could always revert back I guess. I provided my lspci as I remembered that might be useful.

---

### Post by Yellow Pasque on 2017-11-08
Could be a DNS issue? As a test, try to ping Google's DNS server:
```
ping -c 5 8.8.8.8
```

---

### Post by el canadiano on 2017-11-08
> **Temüjin said:**
> Could be a DNS issue? As a test, try to ping Google's DNS server:
```
ping -c 5 8.8.8.8
```

It seems to be working tonight, but not the last two nights for some reason.

---

