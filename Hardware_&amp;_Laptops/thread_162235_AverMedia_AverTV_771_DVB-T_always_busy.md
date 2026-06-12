---
title: "AverMedia AverTV 771 DVB-T always busy"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by barbex on 2006-04-18
I successfully installed the AverMedia AverTV 771 DVB-T card on my Ubuntu (Kernel 2.6.12) and I have watched TV with xine and mplayer.
Then I installed a lot of things, mythtv among it and it was still working fine.

Now it doesn't work anymore, I don't know what has caused it. Mythtv can not connect to the device anymore and says that the resource is busy. I did an strace on xine and mplayer for dvb://[Name] and found this:
```

open("/dev/dvb/adapter0/frontend0", O_RDWR|O_LARGEFILE) = -1 EBUSY (Device or resource busy)

```

How can I find out, what process keeps using the device? And how do I kill it? I'm fairly new to Linux so if there is a trick for that I would love to learn about it!

---

