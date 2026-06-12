---
title: "Network problems with Fitz!Box Fon WLAN router"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by krist on 2006-01-07
I'm having problems connecting a computer (ordinary i386) of a friend to his Fritz!Box Fon WLAN router over ethernet/cable using Ubuntu. The connection needs to be set up manually and is very unstable.

When booting (with a live cd, during installation and off a finished install on hd) the router doesn't reply to the dhcp requests, the init process cancels the attempt after 1 minute with a timeout.

Though once the system is up and running I can reach the router by manually issuing "dhclient eth0" or assigning a static IP to the interface. However the connection is very unstable. In most cases 10-20 % of the packets get lost. Ping requests to the router take 300-700 ms and 1300-3000 ms in alternating pairs (e.g. during a ping probe 1st packet ~300 ms, 2nd ~1300 ms, 4th ~300 ms, 5th ~1300 ms, and so on). The delay should be ~2 ms. The interface doesn't show any RX or TX packet errors.

The router itself is working correctly for sure and all live cds (Knoppix, Morphix, Insert) I have tried as well as WinXP from which the owner wants to get rid off are working flawlessly.

So far I have tried the following steps without success:
[LIST]
[*]Installed 3 different network adapters with different chipsets
[*]Tried 5 different Cat5 cables
[*]Installed Hoary instead of Breezy
[*]Disabled IPv6 (according to the [Wiki](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4), additionally used "alias ipv6 off" and checked that the according module isn't loaded)[/LIST]
Because the owner of that box couldn't do without internet any longer and still wants to get rid of Windows I have provisionally installed Knoppix to hd. But because its user-friendlyness I still want to get Ubuntu running there. 

Does anybody know what the problem could be?

---

