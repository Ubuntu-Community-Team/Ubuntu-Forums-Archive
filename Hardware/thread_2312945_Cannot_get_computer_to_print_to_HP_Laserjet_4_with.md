---
title: "Cannot get computer to print to HP Laserjet 4 with aftermarket parallel port card"
date: 2016-02-08
forum: Hardware
---

### Post by delta410 on 2016-02-08
I'm running an AMD Athlon(tm) II X2 240 Processor × 2 system with 2 GB of RAM and Ubuntu 14.04 LTS. The machine does not have a parallel (LPT) port, so I've installed an aftermarket parallel port card.

I manually installed my printer, and it shows up in all the print dialogue windows. I've tried printing documents, and while everything appears to function normally, I get no printout.

Here's part of what lspci shows:

```
david@david-Z1-7309:~$ lspci
[ other items omitted ]
01:0a.0 Serial controller: Oxford Semiconductor Ltd OX16PCI952 (Dual 16950 UART)
01:0a.1 Parallel controller: Oxford Semiconductor Ltd OX16PCI952 Integrated Parallel Port
```

My machine apparently SEES the card, but for some reason, will not USE it. My printer is good, because it prints just fine from my other machine, which runs Windows 7.

I've looked for Linux drivers for this card, but there don't appear to be any.

Is there a way to make this parallel port card work on my machine? Or will this card just not perform under Linux? If it's the latter situation, which brands and models of parallel interface cards have people here used successfully?

---

### Post by mörgæs on 2016-02-24
[http://www.drivers-download.com/en/downloadlist.php?id=164](http://www.drivers-download.com/en/downloadlist.php?id=164)

---

### Post by delta410 on 2016-02-24
Thank you for the information. Don't know why I didn't find it myself. I'll give their drivers a try.

---

