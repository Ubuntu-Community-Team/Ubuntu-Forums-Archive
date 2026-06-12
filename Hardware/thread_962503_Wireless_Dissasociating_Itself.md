---
title: "Wireless Dissasociating Itself"
date: 2008-10-29
forum: Hardware
---

### Post by oxsyn on 2008-10-29
Using 8.1 RC, updated, on my Asus M70.  The wireless card has an atheros chipset.

> xxxx@xxxxx:~$ dmesg | grep wlan0
[   29.762849] wlan0: authenticate with AP 00:02:8a:78:c0:08
[   29.764550] wlan0: authenticated
[   29.764552] wlan0: associate with AP 00:02:8a:78:c0:08
[   29.766273] wlan0: RX AssocResp from 00:02:8a:78:c0:08 (capab=0x421 status=0 aid=233)
[   29.766274] wlan0: associated
[   30.953073] wlan0: disassociating by local choice (reason=3)
[   35.424125] wlan0: No ProbeResp from current AP 00:02:8a:78:c0:08 - assume out of range
[   95.628523] wlan0: authenticate with AP 00:1c:10:19:86:c7
[   95.828043] wlan0: authenticate with AP 00:1c:10:19:86:c7
[   96.028104] wlan0: authenticate with AP 00:1c:10:19:86:c7
[   96.228081] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out
[  120.653270] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  120.852076] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  121.052082] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  121.252122] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out
[  139.517262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  214.836220] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  215.032079] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  215.232079] wlan0: authenticate with AP 00:1c:10:19:86:c7
[  215.432078] wlan0: authentication with AP 00:1c:10:19:86:c7 timed out

Works on the same machine, when I boot into windows.

---

### Post by oxsyn on 2008-10-31
Still no wireless, same problem:

> $ dmesg | grep wlan0
[   27.427978] wlan0: authenticate with AP 00:02:8a:78:c0:08
[   27.437924] wlan0: authenticated
[   27.437927] wlan0: associate with AP 00:02:8a:78:c0:08
[   27.439474] wlan0: RX AssocResp from 00:02:8a:78:c0:08 (capab=0x421 status=0 aid=225)
[   27.439477] wlan0: associated
[   27.451352] wlan0: disassociating by local choice (reason=3)
[   48.243550] wlan0: No ProbeResp from current AP 00:02:8a:78:c0:08 - assume out of range
[  120.436805] wlan0: authenticate with AP 00:02:8a:78:c0:08
[  120.637044] wlan0: authenticate with AP 00:02:8a:78:c0:08
[  120.846574] wlan0: authenticate with AP 00:02:8a:78:c0:08
[  121.044072] wlan0: authentication with AP 00:02:8a:78:c0:08 timed out
[  162.700688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14806.247910] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.445045] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.644083] wlan0: authenticate with AP 00:02:8a:78:c0:08
[14806.844074] wlan0: authentication with AP 00:02:8a:78:c0:08 timed out


Help, please? :)

---

### Post by oxsyn on 2008-10-31
Here's the model number of the card:03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

It's a very new chip.  It wasn't supported by the kernel in 8.04.

---

### Post by oxsyn on 2008-10-31
After a little more searching, I noted that the only wireless drivers around that support my chipset is the ath9k.

> And I am using them: f4rr4r@neutron:~$ lsmod | grep ath9k
ath9k                 296120  0 
mac80211              253440  1 ath9k
f4rr4r@neutron:~$ 


Any suggestions?

---

### Post by hopesdevid on 2008-10-31
i will check and then give you reply

---

