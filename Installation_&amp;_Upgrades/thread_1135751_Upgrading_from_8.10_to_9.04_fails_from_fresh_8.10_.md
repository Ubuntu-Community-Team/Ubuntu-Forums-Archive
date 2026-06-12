---
title: "Upgrading from 8.10 to 9.04 fails from fresh 8.10 install."
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ubuntuforums on 2009-04-24
I connect to my server through ssh. My host doesn't have an Ubuntu 9.04 template yet (and won't 3+ weeks), only 8.10 (minimal). So I reinstalled 8.10, got all updates, then tried to upgrade to 9.04, I get the three errors below. The upgrade finishes, but when the server reboots, it never starts back up.

I also tried not doing any 8.10 updates, and just immediately upgrading to 9.04, same thing.

```

* Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)... 
   error: "Operation not permitted" setting key "kernel.printk" [fail]

* Setting kernel variables (/etc/sysctl.d/10-network-security.conf)... 
   error: "Operation not permitted" setting key "net.ipv4.tcp_syncookies" [fail]

* Starting kernel log daemon... [fail]

```

How can I upgrade from 8.10 to 9.04 and avoid these errors?

---

### Post by ubuntuforums on 2009-04-25
I take it I'll just have to stay with 8.10.

---

