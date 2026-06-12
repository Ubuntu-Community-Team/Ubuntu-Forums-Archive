---
title: "Gmail don't open in Firefox or Konqueror"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by hsalgado on 2009-05-02
Hi Friends, I am having a hard time trying to solve this problem, so I better ask you.

After I upgraded to Kubuntu 9.04 firefox nor Konqueror open any google address.  This is particularly important for reading my e-mail at gmail.

The error says that [www.google.com](www.google.com) can not be located in the internet.  I try with other machines in my network and I don't have any problem.

Any thoughts would be greatly appreciated.

Many thanks!

HuGOL.

---

### Post by cariboo on 2009-05-02
Sounds like you are having dns problems. Check /etc/resolv.conf, note the spelling, and check the nameserver addresses to see if they match the ones that your isp provides. You could also try [OpenDNS]("http://www.opendns.com/start/"), to see if that solves your problem.

---

