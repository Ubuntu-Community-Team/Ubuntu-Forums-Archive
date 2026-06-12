---
title: "Ubuntu Server install freezes on VIA Nano Mini-ITX board"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by pimpalaputty on 2009-10-19
Hi!

I try to install Ubuntu Server 9.04 to [this board]("http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=585&proname=NF76-N1GL-LF").

The install progress freezes on this line:
```
1.934015 PCI: Using ACPI for IRQ routing
```

I've tried various switches: noapic,nolapic,acpi=noirq,acpi=off,irqpoll. The result is the same (freeze), just the logmessages change a little.


Suggestions?

Thanks, pimpalaputty

---

### Post by prshah on 2009-10-19
> **pimpalaputty said:**
> 
Suggestions?

The board you are using has a RealTek 8111c gigabit onboard ethernet.

Apparently there are known problems with this (which are solvable), but first you need to confirm if this is actually the problem, or if it is something else.

You can do this by disabling ethernet in the BIOS options, and then checking if Ubuntu server is able to boot. 

If it is, I suggest you Google for how to find / enable the correct driver for this ethernet. Post back if you have difficulties.

If the board still refuses to boot even with ethernet disabled, I have no suggestions for you; maybe someone else can help.

---

### Post by pimpalaputty on 2009-10-26
It's still freezes.

---

