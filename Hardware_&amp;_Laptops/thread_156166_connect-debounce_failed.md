---
title: "connect-debounce failed"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by cbhargava on 2006-04-06
I am using Ubuntu 5.10 (32 bit SMP) for a long time and have got this error twice. ](*,) 

[4295080.371000] hub 5-0:1.0: connect-debounce failed, port 7 disabled
[4295081.931000] hub 5-0:1.0: connect-debounce failed, port 8 disabled
[4295083.491000] hub 5-0:1.0: connect-debounce failed, port 7 disabled
[4295085.051000] hub 5-0:1.0: connect-debounce failed, port 8 disabled
[4295086.611000] hub 5-0:1.0: connect-debounce failed, port 7 disabled
[4295088.171000] hub 5-0:1.0: connect-debounce failed, port 8 disabled
[4295089.731000] hub 5-0:1.0: connect-debounce failed, port 7 disabled
[4295091.301000] hub 5-0:1.0: connect-debounce failed, port 8 disabled

This error keeps on filling logs and dmesg and it knocks out the network port. My hardware is:

Intel D945GNTLR motherboard
Pentium D 820 CPU
1GB Memory
Onboard NIC
SATA WD drive
nothing on PCI slots


This error crops up suddenly (no hardware change, no USB connect or disconnect) while browsing. The network dies. Last time it persisted even after a few restarts. I had to use a 3C905C and use that over my onboard Intel NIC. :-k 
After a few days I checked, it was gone.

Tried to reach Intel support but they bluntly said that they don't support Ubuntu or Debian. I would have to reproduce this error on RHEL. ](*,) 

Any help would be appreciated.

Regards,

---

