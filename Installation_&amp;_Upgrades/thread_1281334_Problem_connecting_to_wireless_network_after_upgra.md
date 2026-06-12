---
title: "Problem connecting to wireless network after upgrading to Ubuntu 9.04"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by chkhurum on 2009-10-03
I upgraded from 8.04 to 9.04 but found out that my wireless connection is not working. It used to work in 8.04 version. My system does not detect any wireless connection, previously it used to detect automatically. 


Details of system and network:
May laptop is Lenevo X61s and my using[B] 
$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

$ uname -a
Linux Khurum-ThinkPad 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/Linux

[/B]By doing following gives no errors.
[B]$ modprobe mac80211
$ modprobe iwl4965[/B]

When I use Network manager tool to configure wireless network manually even then it does not connect to any wireless network.

Does anyone knows how to solve wireless problem? 
Thanks.

---

