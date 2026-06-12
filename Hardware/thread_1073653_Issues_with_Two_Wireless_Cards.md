---
title: "Issues with Two Wireless Cards"
date: 2009-02-18
forum: Hardware
---

### Post by 9a8sy on 2009-02-18
I have a Gateway laptop with an internal Realtek 8187 wireless card. I believe there is something wrong with it as it will only show about 20% connection status and there is very slow response time if it even connects at all. I have installed a Linksys WRT54GS card and seems to work well.

My problem is that I cannot turn off the internal card and when I connect wirelessly, both cards attempt to connect. This seems to cause other issues. How do I either force the internal card to not connect or if necessary, how to I remove or "Blacklist" it?

---

### Post by 9a8sy on 2009-02-18
I forgot to mention I'm running Ubuntu 8.1

---

### Post by cariboo on 2009-02-18
You may be able to turn off your onboard wireless card in the BIOS, other wise add the driver for the adapter to /etc/modprobe.d/blacklist. I'm not sure what driver the card uses, but you can check by running in an Aplications-->Accessories-->Terminal

```
sudo lshw -C network
```

Jim

---

