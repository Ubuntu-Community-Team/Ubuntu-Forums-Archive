---
title: "Dell Inspiron 5000 crashes"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by fusiachi on 2007-03-17
Hi,

I've had an old laptop (Inspiron 5000) running Xubuntu 6.10 for a few months now, for my mother to use back at home for basic web browsing, word processing, solitaire, etc...  When visiting home over spring break, it started to act up.  It just freezes; a complete freeze w/no way out short of a hard reset.  It'll reboot (most of the time), and run sucessfully for 4 or 5 minutes, then it just freezes up.  Is there a log or something somewhere that might lend insight into what's going wrong?

I'm guessing something hardware-wise is on its last legs, but I'm open to any suggestions.  I'll post any additonal required information upon request.

Thanks.

-wade

---

### Post by dentonlt on 2007-03-17
Does it do the same off a CD?
There is another thread here that might be caused by overheating.  Could be your problem, too.

I don't know enough to tell you whether all the system logs are dumped on reset.  Perhaps watch dmesg as it approaches a crash, or 'tail /var/log/syslog'.

?

---

### Post by fusiachi on 2007-03-17
Yes, it does the same thing when booting from a CD.

Heat seems like a possible culprit, maybe.

---

