---
title: "bcm4318 problems connecting to &quot;weak signal&quot; wlans"
date: 2009-07-12
forum: Hardware
---

### Post by acimmarusti on 2009-07-12
My issue related to wireless is that with the newest b43 firmware loaded, Network-Manager sometimes behaves abnormally with certain weak-signal wireless networks. For example, whenever I visit my girlfriend and I try connecting to her wireless network (which is very weak and sluggish with any OS!), Network-Manager will initially detect the network, connect to it briefly (matter of seconds) and then suddenly the signal strength will go to 100% and then immediately to 0% and it will disconnect. Any further attempts to reconnect are futile. Upon restarting the system the same situation will arise. The curious thing, is that if I load the older b43 firmware (meant for kernels <= 2.6.25), Network Manager successfully connects to the network and doesn't lose the connection (in fact, it works so well, that her laptop with winxp often fails to load online videos while mine does it efficiently). Unfortunately, using the older firmware comes with a steep price... the most important issue being, it leads to kernel panics and freezes (random) and the download and upload speed is also slightly diminished... Have you had any experience with these issues? (in the past I have been able to stop the kernel panics a little bit by installing the backported modules, but I would rather use the newer firmware)

---

