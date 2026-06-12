---
title: "Ping works, Firefox doesn't"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by raja2 on 2006-01-09
I'm not able to get Firefox working on my Ubuntu laptop (or desktop) at home. I have an ActionTec DSL Router/Wireless setup at home. Windows and Powerbook work fine, but the Ubuntu systems aren't.

"ping" works. but the browser doesn't. However, if I ping the same address beforehand, then the browser works... Pinging each URL in a terminal just before browsing it, is getting tedious. I don't think it is just Firefox. Doing a urllib.urlopen('URL') from python timesout as well.

Thanks in advance for any help.. If there are configuration details I can check on Powerbook and use the same ones for Ubuntu, please let me know.

Thanks,
Raja

---

### Post by gsdefender on 2006-01-09
Maybe the problem is in the DNS resolver file. Could you post the content of your /etc/resolv.conf?

---

### Post by earobinson on 2006-01-09
what are you pining, try to go there with firefox (shouldent ping and firefox use the same /etc/resolv.conf settings? (still post them)

---

### Post by dcstar on 2006-01-09
[QUOTE=raja2]I'm not able to get Firefox working on my Ubuntu laptop (or desktop) at home. I have an ActionTec DSL Router/Wireless setup at home. Windows and Powerbook work fine, but the Ubuntu systems aren't.

"ping" works. but the browser doesn't. However, if I ping the same address beforehand, then the browser works... Pinging each URL in a terminal just before browsing it, is getting tedious. I don't think it is just Firefox. Doing a urllib.urlopen('URL') from python timesout as well.

Thanks in advance for any help.. If there are configuration details I can check on Powerbook and use the same ones for Ubuntu, please let me know.

Thanks,
Raja[/QUOTE]
about:config

Find network.dns.disableIPv6, set to True.

Also search these forums for "disable ipv6" instructions.

---

### Post by gravediggers on 2006-01-09
[QUOTE=dcstar]about:config

Find network.dns.disableIPv6, set to True.

Also search these forums for "disable ipv6" instructions.[/QUOTE]

That worked for me for the same problem. The actual cause is a little deeper, but that solution gets around the problem nicely!

---

### Post by raja2 on 2006-01-10
Thanks for the suggestions here, things are working fine now!!

I checked /etc/resolv.conf.  I deleted these first two lines:
  search domain.actdsltmp
  nameserver 192.168.0.1   (my dsl router)

with just one line left for the nameserver returned by my ISP and Firefox works like a charm now... Don't know how "ping" was working, but I wouldn't worry about now.

Raja

---

