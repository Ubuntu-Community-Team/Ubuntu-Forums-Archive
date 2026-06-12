---
title: "Broadcom ethernet non-wifi bcm4401 only 1.5 MBytes/sec"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by HubertB on 2008-02-18
Hi!

I've got some problems with a bcm4401 ethernet nic (driven by the b44 linux kernel module): It only transmitts about 1.5 Megabytes per second over a switched 100BaseTX Ethernet.

I first detected this problem when copying large files over nfs, so I thought it might be a nfs-related problem. To exclude that, I measured the speed with the command line tool "iperf" => Same issue, only about 1.5 Megabytes per second :-(

Any ideas?

Further information: Ubuntu 7.10, system is a Fujitsu-Siemens Lifebook S2110.

---

### Post by HubertB on 2008-02-18
Update: After suspending the laptop and waking it up again, the bcm4401 nic works as it should:

After a normal system boot:
```

$ scp desktop:/home/hubertb/Desktop/jdk-6-doc.zip .
hubertb@desktop's password: 
jdk-6-doc.zip                                 100%   52MB **261.5KB/s**   03:25

```

After suspend and wakeup:
```

$ scp desktop:/home/hubertb/Desktop/jdk-6-doc.zip .
hubertb@desktop's password: 
jdk-6-doc.zip                                 100%   52MB   **8.7MB/s**   00:06

```

The question now is: Whats different after waking up from suspend? I need some help with further investigation.

---

