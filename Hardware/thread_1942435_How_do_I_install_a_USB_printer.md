---
title: "How do I install a USB printer?"
date: 2012-03-17
forum: Hardware
---

### Post by Amurko on 2012-03-17
Running 11.10, I have no idea how to install a USB printer.

What I've tried:

1) Going to [http://localhost:631/admin](http://localhost:631/admin)

Select "Add Printer"

Problem is, no USB option is listed.  There's only LPT1.

2) Here's my lsusb output:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 111d:0000  
Bus 001 Device 003: ID 0ac8:3313 Z-Star Microelectronics Corp. 
**Bus 001 Device 004: ID 04b8:0803 Seiko Epson Corp. Printer (Composite Device)**
Bus 003 Device 002: ID 6993:b001 Yealink Network Technology Co., Ltd. VoIP Phone

```

What do I do now?

---

### Post by Cheesehead on 2012-03-17
It's not asking "Where is the printer plugged in?"

It doesn't care about USB vs Serial vs Parallel ports. They're all just Local (LPT/LPR). The only thing it cares about is Local vs Network. And you already specified Local.

It's asking "Here's what I found. Which one is it?"

As long as your printer shows up among the Local printers (top of the list), just select it. It it doesn't print, let us know.

---

### Post by Amurko on 2012-03-17
> **Cheesehead said:**
> It's not asking "Where is the printer plugged in?"

It doesn't care about USB vs Serial vs Parallel ports. They're all just Local (LPT/LPR). The only thing it cares about is Local vs Network. And you already specified Local.

It's asking "Here's what I found. Which one is it?"

As long as your printer shows up among the Local printers (top of the list), just select it. It it doesn't print, let us know.

Seems the problem is more complicated..

I upgraded to the 12.04 beta (update-manager -d) and now the printer is found!

---

