---
title: "Realtek RTL8187b wifi vs. Ubuntu 9.10"
date: 2009-12-11
forum: Hardware
---

### Post by obalix on 2009-12-11
Hey every1,

I have a Toshiba L40 notebook with a Realtek RTL8187b wlan card. I installed ubuntu 9.10 3 days ago. Its great, it recognized my wlan card, I can connect to my wpa2 encrypted router, it is really great. BUT. If I use torrent (for example deluge) after a few minutes my connection is dead. I mean literally. My connection is dropped, I see my router on the wireless connection list, but I cannot connect to it... even if I restart my notebook. The only solution is if I reset the router. I thought that is a router issue. But guess what, my father's notebbok has win7 on it, and I used that for about 3-4 hours, with maximum speed torrent download, and it worked like a charm.

Next I suspected deluge, so I tried vuze, transmission, qtorrent...etc. Same result, all killed the connection.

I am a beginner ubuntu user, I did not try new wlan drivers or sg like that, because I don't know if it is the problem, or how to do it anyway.

Do you have any suggestions?

---

### Post by obalix on 2009-12-12
up :)

---

### Post by wangsuda on 2009-12-12
I had a problem similar to that with a Realtek card as well. What I did was allow dynamic IP settings, but a static DNS setting (through OpenDNS). I don't know why, but it worked like a charm.

---

### Post by obalix on 2009-12-12
I don't know what is openDNS, but I will check it out
thanks for your reply

---

### Post by wangsuda on 2009-12-12
> **obalix said:**
> I don't know what is openDNS, but I will check it out
thanks for your reply
[www.opendns.com](www.opendns.com)

---

### Post by jinbatsu on 2010-01-28
I have the same problem here!
I use my Laptop Toshiba Satellite A215-S7447
Wireless: Realtek RTL8187B.

Using Ubuntu 9.10 Karmic Koala.
Deafult Installation Ubuntu detect the Wireless as RTL8187, it work and connected to the wireless, sometimes connect to internet (but very slow!!), and sometimes cannot connect to the internet.

And I try to install Windows Wireless Driver, but still no luck!

@wangsuda, how you setup openDNS? can you explain? thanks.

---

### Post by mrgoldy on 2010-01-28
I had the same problem(not with your Realtek device) with Transmission running and then my connection collapsing.

I selected all forms of the updates(security, proposed, and the third one, forgot what it was)

Everything worked fine after that.

---

### Post by jinbatsu on 2010-01-28
OK, now i know how to use [www.opendns.com](www.opendns.com)

But, now how to get back my previous wireless driver?
Please help.

Thanks.

---

