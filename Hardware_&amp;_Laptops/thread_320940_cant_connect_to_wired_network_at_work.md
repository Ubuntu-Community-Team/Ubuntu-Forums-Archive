---
title: "cant connect to wired network at work"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by robi on 2006-12-18
Hi!

I can't connect to wired network at work or any other than my home network with my laptop acer 5101. Network manager says it is connected to wired network, but when i open firefox page wont load. I have no problem connecting at home to wireless or wired network.

---

### Post by hal10000 on 2006-12-18
Maybe at work you have to use dhcp while at home you have a static ip-address (or the other way)? If so, you can create a new profile with your network-admin.
You can then use one at home and the other on work.

---

### Post by dalonso on 2006-12-18
Hi, in many jobs networks are fixed ip and mac based, that is, only the computer of the firm can connect to the network. Obviously network manager reports a physical network attached to other computer but it cannot get a link, and if it gets a link it cannot get content served.

Have you verified if this applies to your work network?

---

### Post by robi on 2006-12-18
I had no problem connecting at work when i was runing win xp. I'm using dhcp.

---

### Post by hal10000 on 2006-12-18
When next time at work you can try a [COLOR="Red"]ping [www.google.com](www.google.com)[/COLOR] (oe any other site), if this works but your firefox won't, then it's likely to be a nameserver-problem. Look into /etc/resolv.conf at home and at work and compare the content.

---

### Post by robi on 2006-12-20
I looked in my etc/resolv.conf at home, and it looks it is the same like at my friend where i tried to connect. Ping also did not work

this is the content of etc/resolv,conf

search Belkin
nameserver 192.168.2.1


 it is  my home router and his ip.

---

### Post by hal10000 on 2006-12-20
If at work there appears the same entries in /etc/resolv.conf then this is the problem. I will figure out what dhcp-settings you have to use, so that this file will dynamically be overwritten accoring to your demands; as a workaround at work you can add two lines to /etc/resolv.conf:
```

search Belkin
search your.work.net
nameserver 192.168.2.1
nameserver 111.222.333.444

```
You have to edit /etc/resolv.conf with sudo: [COLOR="Red"]sudo gedit /etc/resolv.conf[/COLOR]
You may ask your Administrator at work for the correct ip-Address and name of the network to search. Possibly you may omit the second search entry, depending on how your works network is configured.

---

