---
title: "Can't connect with 3COM PCMCIA 3crxjk10075 after upgrading to 9.10"
date: 2009-10-31
forum: Hardware
---

### Post by retek on 2009-10-31
Hi all, i'm new in this forum =)
I've this wireless card on my "old" laptop.
It works perfectly in the 9.04, thanks to a restricted driver, but can't get it work with the 9.10.
I know this kernel use a new system for restricted drivers (or not?): i can't see any *restricted package in the repositories.
I think the system can "see" the card. Here is the lspci:
```
02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```But can't see any wireless net with wicd.
Any help?
Tell me if you need more info.
Thank you =)

---

### Post by retek on 2009-10-31
Solved thanks to [this thread]("http://ubuntuforums.org/showthread.php?p=8205387#post8205387")
I just comment a line in the /etc/mobprobe/blacklist-ath_pci.cong file :)

---

