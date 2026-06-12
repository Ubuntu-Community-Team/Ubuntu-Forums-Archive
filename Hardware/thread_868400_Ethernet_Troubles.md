---
title: "Ethernet Troubles"
date: 2008-07-23
forum: Hardware
---

### Post by eddygazilion on 2008-07-23
Alright, hello, well, as the topic says, I am having some severe troubles with an ethernet card in a laptop my family has recently acquired. For some reason, it simply does not see it there. Now this is odd, because lspci sees it as some sort of ethernet device, here's the output:

```
2:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
```

In case anyone was wondering if it's some sort of way obscure laptop from Afghanistan or something, it isn't, it's a Toshiba Satellite M305D-S4831. If anyone is familiar with this lappy or knows anything about getting strangely behaving ethernet cards working, I'd appreciate it.

Thanks!
-Eddy

---

### Post by Dark_Stang on 2008-07-23
Check this post...
[https://bugs.launchpad.net/ubuntu/+bug/239852](https://bugs.launchpad.net/ubuntu/+bug/239852)

---

### Post by eddygazilion on 2008-07-24
Aha! That seems to have worked! Thanks!

---

### Post by kvdbreem on 2008-07-26
Yeah, same here.  I ingeniously forgot to test drive the networking on my live instance before installing.  Not that I really wanted to keep that god-awful Windoze Vista.  I was through with it after waiting for hours for the setup and crap!

---

