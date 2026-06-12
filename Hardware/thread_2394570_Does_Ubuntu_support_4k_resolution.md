---
title: "Does Ubuntu support 4k resolution?"
date: 2018-06-18
forum: Hardware
---

### Post by geeky-1 on 2018-06-18
Has anyone successfully run Ubuntu in 4k? I'm thinking of upgrading to a 4k monitor and a card capable of displaying 4k (or just build my next computer with a 4k capable card and monitor), but heard a rumor that Ubuntu might not support 4k yet.

---

### Post by oldfred on 2018-06-18
You need current kernel & drivers.
The 18.04 uses 4.15 kernel, so supported for many versions, since 4.3.
But hardware & drivers can be an issue.

       18.04 4K monitor only works at 30hz on one HDMI port on monitor
[https://ubuntuforums.org/showthread.php?t=2391240](https://ubuntuforums.org/showthread.php?t=2391240)
Have Troubles With 4K Displays On Intel Linux? Try The Linux 4.3 Kernel
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix)

---

### Post by arsenic23 on 2018-06-19
I had no troublerunning 4k on the on chip video of an Intel G4500 for a while now using 16.04.  Kernel versions have a huge impact on performance.  Right now I have no issues with playing any video on it other then 1080 or above 10bit, but I doubt that little budget CPU/GPU could do that with any amount of tweaking.  Honestly thought, realizing that I was never actually watching 4k video on it I went back to 1080 so that I could watch 10bit files; I'm using it as a set top system.

I tried a lot of different kernels, and, at least for the video on the G4500, I found that I got the best performance out of 4.7.0.

I don't know if anyone will find this information useful, but maybe it'll stop someone with on chip Skylake having to spend an entire evening testing different kernels.

---

