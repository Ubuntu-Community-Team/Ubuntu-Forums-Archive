---
title: "Ralink 2870 and Ralink 3072 USB Wifi Adapters working, but causing kernel panic"
date: 2014-05-18
forum: Hardware
---

### Post by weiss-nikolaus on 2014-05-18
Hi All,

To begin with, I just wanted to point out that I'm a beginner when it comes to Ubuntu (or Linux in general). I'm running Ubuntu 14.04 LTS on a 64 bit Intel i3 quad core machine.

I recently bought 2 USB wifi adapters for my pc, and both of them work for about 30-90 minutes, and then cause kernel panic. On the kernel panic screen, it repeatedly mentions the drivers for my wifi adapters. Also this only happens when I plug in the adapters, so they are causing it for sure.

The chipsets are Ralink 2870 and Ralink 3072. The drivers for both are included in the firmare when you install Ubuntu (rt2870 and rt3000), and as I mentioned above, when I first plug them in, they are immediately recognized, and function perfectly until the system crash. Just in case, I manually installed the latest drivers, but since these are from 2012, I'm assuming that they were the same as the ones that already came bundled with the OS. One of them came with a disk with drivers on it (which seemed to be same as some of the older drivers on the Ralink support page), but when I followed the step by step instructions, and eventually ran 'make' and 'make install' I got errors, and wasn't able to set it up (I assumed this was because they were made with a much older version of Linux in mind). Like I mentioned, though, I already installed newer drivers.

I have found one old forum post from a year ago, on another forum, with a few users listing exactly the same symptoms, but no one had a solution. Other than that, there are plenty of posts about getting the Ralink chipset to work, but that's not my issue. The wifi adapters work, they just crash after a while.

Any help would be appreciated (if you can't help directly but tell me where I could ask for more help, that would be great, too). If you need any extra info please let me know.

---

