---
title: "Ubuntu flash pen install, not portable"
date: 2010-11-09
forum: Hardware
---

### Post by victor.cighir on 2010-11-09
Hello, I installed Ubunutu 10.10 off a livecd to a 16gb flash pen with multiple partitions. It's working fine except for one thing: I cannot have graphics reconfigured on a Acer Aspire 5100 laptop with ATI Radeon Mobility X1300 video card. 

I had the pen on a desktop PC with a NVidia Geforce 5500 card and it worked flawlessly. Now I moved around my pen to this laptop. It used to be no problem because I could install the proprietary ATI drivers with Jockey and everything was ok. 

Now I cannot get the opensource drivers for ATI working.

I have to add, that after installing 10.10 on the same laptop with wubi, acceleration works just fine.


2nd problem I noticed, wireless is working on the pen, but not on the freshly installed Ubuntu.


So, the question is: how to reconfigure graphics?

```
$lspci -nn
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M52 [Mobility Radeon X1300] [1002:7149]

04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```


Thanks!

---

