---
title: "NetworkManager &amp; DNS"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by FuriousLettuce on 2006-03-20
I have been having various trouble with my network interfaces not being able to resolve addresses. NetworkManager auto-creates /etc/resolv.conf with nameserver set to 127.0.0.1, when I actually want it to be 192.168.1.1 (it should do it automatically). Changing resolv.conf to contain 192.168.1.1 then allows links2 to resolve anything - I assume that it loads the new resolv.conf on load. However, epiphany and firefox are left only being able to visit websites that have already been resolved by links2 (using NetworkManager's caching nameserver I assume).

I wondered if there was any way to get NetworkManager to properly find and enter the correct DNS into /etc/resolv.conf, and, if not, is there any way to get firefox / epiphany to take notice of an updated resolv.conf?

Thanks in advance

---

### Post by Zelut on 2006-03-20
[http://ubuntuforums.org/showthread.php?t=147267&highlight=resolv.conf](http://ubuntuforums.org/showthread.php?t=147267&highlight=resolv.conf)

try this fix that I previously helped someone thru.  It may do the trick for you.

---

### Post by FuriousLettuce on 2006-03-20
Thanks, but it doesn't work :S. 

When NetworkManager creates /etc/resolv.conf it doesn't appear to pay any attention to dhclient.conf - it simply writes it the same no matter what. However, if I do stop then start networking then the DNS are prepended to the file. Unfortunately, I still have the problem that firefox / epiphany can only access sites that links2 has :S.

---

### Post by ranf on 2006-03-21
AFAIK when you install `network-manager' `bind9' is installed as well.
So you would have to look into configuring bind to your liking (I don't know much about it though).

---

### Post by FuriousLettuce on 2006-03-21
Got it :D 

I added my DNS servers to /usr/share/NetworkManager/named.conf, now it works fine :D

---

