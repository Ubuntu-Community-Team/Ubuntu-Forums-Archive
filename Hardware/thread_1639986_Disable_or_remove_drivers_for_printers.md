---
title: "Disable or remove drivers for printers"
date: 2010-12-07
forum: Hardware
---

### Post by mathew42 on 2010-12-07
I have a USB canon pixma 4500i printer which works reasonably well under Ubuntu, but I want to use the Canon supplied software to print using Windows XP in a VirtualBox VM.

The problem I have is that if Ubuntu loads drivers for the printer, then the printer appears grayed out in the VBox USB menu. I've tried[LIST]
[*]```
sudo rmmod usblp
```
[*]```
sudo rmmod lp
```
[*]stopping cups
[/LIST]

I'm running Ubuntu 10.10 64bit.

How do I stop Ubuntu loading the drivers or determine which drivers need to be unloaded to free the printer up?

---

