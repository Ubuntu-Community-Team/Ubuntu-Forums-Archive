---
title: "Netgear WG511 v1 Dropping"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by ecliptik on 2005-07-11
I have a Netgear WG511 v1 802.11g card that works in Hoary without any problem except sometimes the card's activity light will become solid orange and the green light will start flashing, losing all network connections. When looking at /var/log/messages I see this:

```
Jul 11 17:52:14 localhost kernel: eth0: timeout waiting for mgmt response
Jul 11 17:52:17 localhost last message repeated 3 times
Jul 11 17:52:17 localhost kernel: eth0: mgmt tx queue is still full
Jul 11 17:52:17 localhost last message repeated 10 times

``` 

All I can do to fix it is de-activate the card and then re-activate it. Normally it works just fine when it's close to the wireless router (also netgear) but when I move it into the next room and I put load on the card it crashes out.

I've done some research on the forums and online, but due to the varying versions of the card there are different solutions. I don't believe I'm using the NDISwrapper, but rather the drivers from prism54.org (which is down at the moment) due to this line in my /var/log/dmesg:

```
Loaded prism54 driver, version 1.2
```

Is there a trick to get this card to be more stable? It worked fine on my old laptop running Debian Sarge, and I even saw the same kernel messages for it. Do I need a newer version of firmware? Newer prism54.org driver? NDISwrapper instead?

Also, not really related to this particulary, but sometimes it will load up an IPV6-over-IPV4 tunnel that shows up as sit0 and just screws up everything, anyway to permantly disable this?

Any suggestions or insights are welcome, thank you.

---

