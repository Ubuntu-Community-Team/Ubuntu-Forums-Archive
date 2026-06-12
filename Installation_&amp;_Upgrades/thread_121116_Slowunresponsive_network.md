---
title: "Slow/unresponsive network"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by BenFrantzDale on 2006-01-24
I installed 5.10 on my laptop. It installed nicely but networking just isn't right.

Networking sometimes sort of works, but it is very slow and spuradic. I thought it might be something IPv6-related as per [this forum discussion]("http://ubuntuforums.org/archive/index.php/t-77686.html"), but following those suggestions didn't help. The most suspicious piece of information I have is that when I ping anything, be it my other computer through a hub or a computer on the other side of the country, the ping responses come in clumps with ping times descending by one second each. That is, I send a ping every second for a few seconds and the responses all come back at once. If I change the ping interval (-i2, for example), the ping times descend by that interval: 29,9450ms, 27,450ms, 25,451ms, 23,451ms, 21,451ms, 19,451ms, etc.

This even happens when I ping the DSL modem, 192.168.1.1.

nslookup is similarly slow, except when it isn't. For example, I just tried nslookup twice and it timed out, then did nslookup again and it took ten seconds. Then I tried it again and it took two seconds. A third time and it timed out.

Similar wierdness happens when this computer is plugged directly into the DSL modem rather than through a hub.


Any ideas?

---

### Post by dazednconfused on 2006-01-24
I can't offer you a solution but your not alone. I'm suffering from exactly the same problem!

Web pages take forever to download, and the mouse pointer intermittently freezes while downloading - I've noticed cpu usage sticks at 100% for a few seconds.

I have a 300Mhz celeron with 196MB ram and 20Gb harddrive, the network card is a realtek PCI card.

---

### Post by BenFrantzDale on 2006-01-24
More information: 


(Again, my laptop (Ubuntu) and desktop (Debian) are connected through a hub to the DSL router.)

I ping the router (192.168.1.1) from my laptop (192.168.1.46) and log the conversation with Ethereal on my desktop. I first see an ARP request from the laptop, then an ARP reply from the modem with its MAC address. This repeats several times (let Q be a request, A be an answer; I see QAQAQAQQQQAAAA.)

Next, my laptop pings the router at its correct MAC address with a reply in about 5ms. On Ethereal, the ping requests and replys go back and forth like clockwork, just as they should. On the Ubuntu laptop, however, I get the same delay followed by a pile of replies as described in the initial post.

Similar things happen when I ping outside IP addresses or do nslookup. It's like my laptop is ignoring packets addressed to it even though the IP and MAC address are correct.

Any ideas?

---

### Post by BenFrantzDale on 2006-01-25
One more piece of information: running route takes about 20 seconds... The first line prints out instantly, the second line takes a while. The lines are:

[FONT="Courier New"]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         dslrouter       0.0.0.0         UG    0      0        0 eth0[/FONT]

---

### Post by cubetime on 2006-01-25
[QUOTE=BenFrantzDale]One more piece of information: running route takes about 20 seconds... The first line prints out instantly, the second line takes a while. <snip>[/QUOTE]

This is most likely being caused by the resolver being delayed by the lagging network.  Try [FONT="Courier New"]route -n[/FONT] and route should return immediately.

---

### Post by BenFrantzDale on 2006-01-25
[INDENT]This is most likely being caused by the resolver being delayed by the lagging network. Try route -n and route should return immediately.[/INDENT]
That worked. Thanks. Any idea why the computer would be ignoring packets addressed to it?

---

