---
title: "Eeebuntu: new upgrade doesn't recognize my wireless"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by spursncowboys on 2009-07-01
When I upgraded to the new 2.6.29 kernel, it did not recognize my wireless. I attached it directly to the modem and it worked, but after upgrading again it still did not recognize my wireless.

---

### Post by zopanp on 2009-07-01
Did you tried to install the necessary drivers?

---

### Post by spursncowboys on 2009-07-01
> **zopanp said:**
> Did you tried to install the necessary drivers?
No, I upgraded kernels. The kernel I was using recognized my wireless.

---

### Post by n00b115 on 2009-07-11
i got same problem. my external wireless adapter edimax ew-7318usg 
iwconfig ==>

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

```eth1 = ipw2200 (internal)
kernel 2.6.28-13-generic

---

