---
title: "Decent PPPoA ADSL Hardware?"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by sjmorgan on 2005-08-02
Does anybody know of any decent PPPoA ADSL hardware that's well supported under GNU/Linux (preferably PCI)?

Right now I'm using a Thompson SpeedTouch 330 USB modem and the drivers for it suck! Not only do I get disconnected frequently (this could be due to my ISP though) but, when I do, I can't reconnect unless I kill pppd, unplug the modem, plug it back in and restart pppd. As you can imagine this gets tired pretty fast.

I know there are plenty of combination ADSL modem/routers out there but I don't want my GNU/Linux box to be sitting behind NAT.

Thanks.

---

### Post by sjmorgan on 2005-08-08
Unanswered threads suck so, for the sake of anyone who might be looking for the same information I was, here's some information I came up with:

[Linux PCI ADSL modem](http://bbs.adslguide.org.uk/showthreaded.php?Board=dslrouter&Number=1587883)
[Sangoma S518 ADSL PCI Card](http://www.sangoma.com/products/p_s518adsl-specs.htm)
[PPPoA ADSL with a Conexant Accessrunner PCI modem](http://gentoo-wiki.com/HOWTO_PPPoA_ADSL_with_a_Conexant_Accessrunner_PCI_modem)

I decided to go for the Sangoma S518 because, although it's pretty expensive, the company that makes it specifically support GNU/Linux as well as FreeBSD and OpenBSD so not only do I forego badly reverse engineered drivers but I'm supporting a company that releases F/OSS drivers. Go me!

---

