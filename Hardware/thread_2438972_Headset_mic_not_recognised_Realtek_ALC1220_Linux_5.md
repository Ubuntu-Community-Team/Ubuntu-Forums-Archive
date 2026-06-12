---
title: "Headset mic not recognised Realtek ALC1220 Linux 5.3 Ubuntu 18.04.1"
date: 2020-03-20
forum: Hardware
---

### Post by ubt-jwh-01 on 2020-03-20
Hi,

I have read more than a dozen "solutions" to this common problem and none have worked.
The common answer is to mess around with alsamixer, hdajackretask and pulseaudio which is not working for me.
I've disabled my internal laptop mic, no other mic is being recognised. 
I have a dual-boot setup, and my headset is working fine on Win10.

Apparently ALC1220 is meant to be supported since the Linux 4.11, so I'm surprised that I have an issue in 5.3.

Here is a link to my ALSA info:
[http://alsa-project.org/db/?f=a5002ee7ce4e930f7d405d1cffe0709c99c1f140](http://alsa-project.org/db/?f=a5002ee7ce4e930f7d405d1cffe0709c99c1f140)


regards,
Jason.

---

### Post by mörgæs on 2020-03-22
Hi, welcome to the fora.
How does 19.10 work?

---

### Post by Yellow Pasque on 2020-03-22
```
Subsystem: CLEVO/KAPOK Computer Device [1558:96e1]
```

You have some sort of Clevo-based laptop (with ID  96e1)
This was supposed to have been fixed in kernel 5.2.x: [https://github.com/torvalds/linux/commit/503d90b30602a3295978e46d844ccc8167400fe6#diff-6cb60ab78549a5b6838f746b9e128105](https://github.com/torvalds/linux/commit/503d90b30602a3295978e46d844ccc8167400fe6#diff-6cb60ab78549a5b6838f746b9e128105)

The only thing I can suggest is filing a bug on [https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&product=Drivers&resolution=---](https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&product=Drivers&resolution=---) or e-mailing the patch author directly.

---

