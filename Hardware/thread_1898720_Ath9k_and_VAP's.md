---
title: "Ath9k and VAP's"
date: 2011-12-22
forum: Hardware
---

### Post by darkdragn on 2011-12-22
I'm experimenting with bridging interfaces, and using the my system as a router. I would like to learn how I can connect to one wireless network, and broadcast a new network on a Virtual Access Point. I already know all of the iptables configurations required, and how to stage a dhcp server. However no amount of google-ing has yielded any positive results on how to properly create a vap that can function independently of the main. I have already tried ```
iw phy phy0 interface add ath0 type __ap
ip link set ath0 address 78:dd:08:ea:6c:07
```

If anyone can help, I would appreciate it very much.

Oh, an if you would like the scenario where this is useful, the free networks in the area require an authentication proxy, just one of those click accept ones, however I would like to connect my 3DS to one of them. Without a web browser, however, this task seems impossible. Thus the re-broadcast on a vap! ^_^

---

