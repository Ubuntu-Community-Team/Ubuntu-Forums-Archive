---
title: "Very slow access to isc.sans.org"
date: 2008-07-21
forum: General Help
---

### Post by JohnnyS987 on 2008-07-21
This is a very odd problem.

Access to the website "http://isc.sans.org" (The SANS Internet Storm Center) is extremely slow. It takes 10 minutes to come up and about 10 minutes more each time I  go to any link at that site.

- Windows systems (Vista and XP) on the same subnet have no problem, whether I use IE or Firefox.
- All systems on the subnet get their IPs from the same DHCP server.
- This happens with both Mozilla Firefox and Lynx (Installed from Synaptic).
- This happens on my current install and when I use Firefox after booting up the Live CD.
- This happens even from other new user accounts and if I clear out $HOME/.java and $HOME/.mozilla
- This started to happen when I upgraded to 8.04.

Any ideas? I will send an email to the webmasters, but is there anything I can check in Ubuntu to troubleshoot this weird problem?

John Sloan

---

### Post by Tim Sharitt on 2008-07-21
Is there anything odd about your internet connection in Ubuntu? I tried it on 8.04 with firefox and it loaded up just fine.

---

### Post by JohnnyS987 on 2008-07-21
Nothing weird that I can see. 

The site isc.sans.org works OK on the same system running WinXP, however it has 10 minute delays when I boot a LiveCD version of Ubuntu 8.04.

Since you are going to the site OK with Ubuntu 8.04 and Firefox, that makes me wonder if it is an ISP thing or some sort of problem between my ISP and the website. I use rogers.com here in Canada, and they have been rumored to mess with web pages to insert content. 

John Sloan

---

### Post by JohnnyS987 on 2008-07-21
Right.

I think I fixed it. The problem seems to have been with firefox wasting time waiting for IPv6 DNS lookups (AAAA) to fail before trying IPv4 lookups (A). Since I don't have any IPv6 networks, this was causing a timeout.

I followed the info here: [http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6) and it all works nice and fast now.

John Sloan

---

