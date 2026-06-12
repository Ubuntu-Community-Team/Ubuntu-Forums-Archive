---
title: "Atheros wireless problems."
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-02-26
Hello I have a Toshiba A135-S2246 with onboard Atheros wireless lan running Ubuntu 6.10 Edgy.  I have a list of 'lspci' below.

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)


The AR5006EG is the onboard wireless land and the AR5005G is the DLink DWL-G630 PCMCIA wireless card.

The PCMCIA cards works flawlessly while the onboard 5006 does not work.  Any suggestions?  I am using the PCMCIA card to post this thread.

Thanks

---

### Post by stchman on 2007-02-27
Anyone?!!!!

---

### Post by Lonthong on 2007-02-27
Try the ng version of madwifi r 1711 or later.
You can download it here:
[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)
Search the forum for install instruction
Here is the thread:
[http://ubuntuforums.org/showthread.php?t=212600&page=3&highlight=atheros+ar5006eg](http://ubuntuforums.org/showthread.php?t=212600&page=3&highlight=atheros+ar5006eg)

---

### Post by mostholy on 2007-04-25
I'm running A135-S4527 via wifi under 7.04 feisty cd-boot (haven't committed to install as I'm still debugging potentials).  No problems with the wifi under this situation, took a bit of setup under system/administration/network to get my home network recognized but from there it was smooth.  To be honest it seems to take two (identical) attempts at configuring the wireless and then it works (have only a few experiences as a baseline).  

Hope this isn't useless, seems to be limited feedback on the A135-S4527.

---

