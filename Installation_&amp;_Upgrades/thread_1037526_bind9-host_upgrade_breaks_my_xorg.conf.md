---
title: "bind9-host upgrade breaks my xorg.conf"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by arqbrulo on 2009-01-11
Hi to all.

The other day, I really felt like backing up my system for the first time before doing any upgrades. It was a good thing too. My system was asking me to upgrade bind9-host, dnsutils, libbind9-40, libdns43, libisc44, libisccc40, libisccfg40, liblwres40 and ntpdate. When I restarted my computer after making those changes, it said that my xorg was not configured correctly. That I was not using the right video driver, or something like that. The point is that after restoring my computer to how it was before the upgrade, and trying to isolate the problem, I noticed that ntpdate had NOTHING to do with my problem. The problem is with bind9-host, dnsutils, libbind9-40, libdns43, libisc44, libisccc40, libisccfg40 or liblwres40. I cannot upgrade just one of them, it's either all or nothing.

I also tryed to remove bind9-host. Synaptic removed bind9-host but installed host instead, and upgraded the other libs. After the reboot it gave me the same problem, so it's not bind9-host either. If I want to completely remove bind9-host AND host, it also wants to remove ubuntu-desktop, wine, and a few other programs that seem important.

My computer is a laptop running Ubuntu 8.10 64bit. I have integrated nvidia card with the 177.82 driver.

I'm not sure if I explained myself clearly, so if there's anybody out there who might be able to help me out but has a few more questions or wants any clarifications, just let me know. Thanks.

---

### Post by arqbrulo on 2009-01-15
Ok, so apparently my nvidia driver was screwing up when I upgraded bind9-host. What I ended up doing is uninstalling my nvidia drivers, upgrading, then re-installing my drivers. And while I was at it, I decided to install the latest drivers directly from the nvidia site.

---

