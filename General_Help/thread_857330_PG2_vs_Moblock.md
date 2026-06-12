---
title: "PG2 vs Moblock"
date: 2008-07-12
forum: General Help
---

### Post by rocker9455 on 2008-07-12
hi im a avid windows user although i dont like microsoft :D anyway i as just wondering how effective how moblock is compared to pg2 in windows pg2 gets many more hits compared to moblock in linux when torrenting with the same torrents ... im using the same lists and have http/https whited out on both programs their properties are the same as far as i am aware could some one please help shed light on this subject?

---

### Post by jre on 2008-07-14
I'm not aware of any differences. With no whitelisting at all both programs should block all traffic to and from the IPs in the blocklists. If this should not be the case I would consider it a bug.

Just some thoughts:

1. Which lists are you using? Remember that my Debian packages don't support lists from php redirects.

2. The differences might origin from the torrent-applications. Maybe the windows one tries to open more connections.

3. With the moblock 0.9 packages outgoing traffic is REJECTed - this means that your torrent application gets notified when an IP that it tried to reach was blocked. Therefore your torrent application will not try any more to coonect to this IP.
I don't know what PG2 does, but maybe it's just something like DROP - in this case your windows torrent-application will not get notified when an IP was blocked and therefore might try to connect to it several times.

You have to make further investigations, e.g. have a look at the log files and try a packet sniffer like wireshark, to find an answer.

jre

---

