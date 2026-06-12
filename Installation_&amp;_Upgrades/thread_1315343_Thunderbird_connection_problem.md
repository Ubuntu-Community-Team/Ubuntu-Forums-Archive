---
title: "Thunderbird connection problem"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by jumpa72 on 2009-11-05
Hi,
I've installed thunderbird 2.0.0.23 on my server, running Ubuntu 9.04 64bit.
I've succesfully imported my mail from my old windows server. It correctly recovers all accounts and password.
My problem is that Thunderbird can't connect to any mail server, and can't send any mail too! 	](*,)
The initial page of TB says it can't connect to internet... my internet connection works fine, I can correctly navigate the web with firefox...
Do you have some idea?
tnx

---

### Post by wrgb2 on 2009-11-05
Check under Edit > Preferences > Advanced under the Network & Disk Space tab, then press the Connection button.  What does it say in there??

---

### Post by jumpa72 on 2009-11-05
> **wrgb2 said:**
> Check under Edit > Preferences > Advanced under the Network & Disk Space tab, then press the Connection button.  What does it say in there??

It is set to Direct Internet Connection. I've tried also automatic proxy configuration, as Firefox, but it doesn't work.
Is it possible to be a firewall related problem?

---

### Post by wrgb2 on 2009-11-05
Could be.  Could be the port settings.  What type of internet connection do you have?

---

### Post by jumpa72 on 2009-11-05
DSL connection via a netgear router. The others windows pc, connected to the same router, works fine.
The Thunderbird account port is 110 for pop3 and 25 for smtp. (standard conf)

---

### Post by wrgb2 on 2009-11-05
If those same settings are working on the Windows PC, it's not the firewall in the router, and i'm using those ports for one of my email servers with Ubuntu without problems.  Only thing I can suggest is that I have one web host that opens up 995 for pop and 2525 for smtp, specifically for firewall issues, you might try those to see what happens.  Can't hurt anything.

---

### Post by jumpa72 on 2009-11-05
Resolved!
I've download manually thunderbird from mozilla's site. I've removed it, and re-installed from synaptics. Now it works fine.
Thanks

---

### Post by wrgb2 on 2009-11-05
Great...when all else fails, reinstall:D

---

