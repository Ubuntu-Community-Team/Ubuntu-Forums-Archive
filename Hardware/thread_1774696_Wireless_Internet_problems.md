---
title: "Wireless Internet problems"
date: 2011-06-03
forum: Hardware
---

### Post by Apocalypse_Alice33 on 2011-06-03
Hey everyone. I installed Xubuntu 10.04 (Lucid Lynx) on my laptop and now I have a dual boot OS. But for some reason, Xubuntu won't pick up on my router, whereas Windows does it automatically. How do I configure it to where it picks it up? I know there's a wireless card in my laptop or else Windows wouldn't detect my router. People on hackforums.net weren't much help either. Thanks!

---

### Post by mikewhatever on 2011-06-03
Hi, and welcome to the forum.

You most probably just need to install the wireless driver for your card. Hook up an ethernet cable for a minute, and you should get a popup prompting for the driver installation. If nothing happens after a minute, open System->Administration->HardwareDrivers from the menu.
In case that doesn't work too, open Applications->Accessories->Terminal and post the outputs of the following command:

```
lspci -nn
```

The output will show the info to troubleshoot the problem, that is, if there is a problem.

---

