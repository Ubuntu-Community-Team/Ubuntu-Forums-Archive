---
title: "Broadcom drivers on Maverick"
date: 2010-10-21
forum: Hardware
---

### Post by mac_untu on 2010-10-21
Hello. My laptop is an hp 6720s.

 Last week i've updated my ubuntu 9.10 to 10.10. I use wubi so i first update it to 10.04 lts and finaly to 10.10.
 In 9.10 broadcom driver were installed without any problem. In  version 10.04 wifi drivers sti ok. However in my ubuntu current version   (10.10) jockey driver manager is asking to activate broadcom drivers  again.


 During the instalation (from 9.0=>10.04=>10.10) i were aked if, due a process of  optimization, the installer woud remove unsued packeges. but i don't  think that was the problem.


 Now jockey is giving this error:


 Sorry, the installation of this driver failled.
 For more details please read registry file: /var/log/jockey.log


 and the registry file says:


 2010-10-21 14:01:59,133 DEBUG: BroadcomWLHandler enabled(): kmod  disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted


 I've tried some manual installations as ndiswrapper but the problem remains.
 Thanks and sorry my english.

---

