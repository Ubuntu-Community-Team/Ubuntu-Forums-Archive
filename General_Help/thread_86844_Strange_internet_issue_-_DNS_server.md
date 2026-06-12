---
title: "Strange internet issue - DNS server"
date: 2005-11-06
forum: General Help
---

### Post by Joch on 2005-11-06
Hi,

Since the installation of Ubuntu I have a strange internet problem. Everytime I start Ubuntu I have to change the dnsserver address (10.0.0.1, also the address to configure my router) into 83.217.75.130. Without the change I cannot access the internet. After some time the address changes back to 10.0.0.1 and have to change it back properly.

I'm using a router (Conceptronic C54APRA). I had the same issue with SuSE, where I had to change the dns-server (like I do under Ubuntu) but their it didn't change after some time.

If you need some more information, please let me know,

Thanks,

Jochem

---

### Post by Remmelas on 2005-11-06
I had similar issues with my setup, as i was running dhcp.  I'm sure there's a better solution for dhcp setups than what i did, but, i disabled dhcp and configured static instead.

---

### Post by Joch on 2005-11-07
I tried what you said, but it didn't help. But thanks nevertheless!

Does somebody else knows what I should do ?

EDIT :

Ok, the problem is solved ! I followed [this]("http://https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29%7C%28server%29") How to. I inserted the DNS-server 83.217.75.130 and now it works !

---

