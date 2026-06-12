---
title: "ASRock Beebox N3150 suspend resume doesnt work"
date: 2015-12-04
forum: Hardware
---

### Post by aniketvb on 2015-12-04
I have Kubuntu installed on an ASRock Beebox N3150(braswell based) mini PC. It is generally working fine, but I am having issues with suspend to RAM. It looks like suspend works fine as syslog seems to show that the system suspended fine, but when I press keys on the keyboard to resume, the power light comes on and the HDD makes a little noise, but the system is frozen totally. after a hard reset, looking at syslog , there is nothing in the log after the suspend event, and I see the logs about the bootup only after that. 

So it looks like the hardware did not signal the CPu/OS to wakup at all, or the OS/Kernel missed, I am not sure!

---

### Post by adrhc on 2016-03-29
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

uname -a
Linux adr-desktop 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

I have the same problem with my Asrock N3150DC-ITX.

---

