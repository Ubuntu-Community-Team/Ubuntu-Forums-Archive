---
title: "Wireless hangs on Asus eeePC 1005HA"
date: 2010-04-29
forum: Hardware
---

### Post by kdorf on 2010-04-29
As the title describes, I use an Asus 1005HA netbook. The wireless card is identified by lspci as:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

When browsing the web, I will frequently (every 1-2 minutes) have a 10 second or so hang where the wireless stalls and does nothing. I remain associated with the access point but pages will not load during this time. If I am pinging something while this occurs, pings will not come back. Interestingly, though, the ping time is not affected by this hang.

EDIT: After some more testing, it seems this only occurs with our encrypted network, UofM Secure, which runs WPA2 Enterprise (PEAP version 0, MSCHAPv2). The unencrypted network (UofM) does not have any hangs from what I can tell (but only tested about 10 minutes worth).

This was also a problem for me in Karmic.

I use the laptop in a university setting where there are many access points, so maybe it is trying to switch between them for some reason?

I have tried installing the latest wireless-compat, ran rmmod ath9k and then modprobe'd it again, but that did not work. I tried connecting to the network with wpa_supplicant, but the issue still presented itself (some suggest the problem is caused by NetworkManager scanning). I also added the user volnanin's PPA to my software sources (he claimed he had patched NetworkManager to fix the scanning) and I am using that -- it *still* does not work.

I'm quite frustrated. Any ideas? I might just have to go back to using ndiswrapper.

---

