---
title: "BitTorrent and iptables weirdness"
date: 2008-10-27
forum: General Help
---

### Post by lovinglinux on 2008-10-27
There is something puzzling me in regard to torrent connections and iptables.

I have no problems with torrent speeds or connections whatsoever, on both directions. I have an iptables rule to open the inbound port in which the torrent client will be listening, an iptable rule to allow ESTABLISHED, RELATED inbound connections and the required outbound rules.

Nevertheless, I still get some inbound blocked connections from peers with connections already established.

For example, let's say my torrent client is listening on port 49152 and it has requested a connection to a peer using the port 53298 as source and the peer is listening on port 6881. Since outbound connections are allowed, the connection is successfully established, listed in the torrent client and also in the netfilter state as ESTABLISHED.

After a while, the peer send me a packet using port 6881 as source and 53298 as destination. It doesn't send to my listening port (49152), because the connection was already established using those ports. So, this packet should be allowed, but I see this connection in the log as blocked. This doesn't happen all the time, but I see a bunch of them in the log.

If the connection to that peer wasn't established yet, I would expect the iptables to block the packet, because my torrent client is listening only on port 49152. In fact, it wouldn't even reach the iptables, because the only port forwarded by the router is 49152. But since the connection was already established and I have a rule to allow ESTABLISHED, RELATED inbound connections to go through, why is it blocked?

Any ideas why this is happening?

EDIT: just to complement...the majority of packets being blocked have ACK or RST flags.

---

