---
title: "A little help with IRQ settings"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by clearzen on 2006-08-02
How do I change IRQ settings for my PCMCIA card. The PCMCIA slot has been freezing my laptop since I put Ubuntu on it. After a little digging with dmesg, grep, and lspci I found that my ethernet card and the PCMCIA slot share an IRQ. I think if I change this the Yenta Driver will stop locking up my PC.

---

