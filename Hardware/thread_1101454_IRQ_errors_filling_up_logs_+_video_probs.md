---
title: "IRQ errors filling up logs + video probs"
date: 2009-03-20
forum: Hardware
---

### Post by Andyukg on 2009-03-20
Hi,


I'm trying to help a friend who is using Ubuntu as I have been working with UNIX type systems for 10 years and am familiar with debian.
The system in question is a desktop core duo based system with ATI 550 graphics. The OS version is Ubuntu 8.10 and previously it has been working without any problems. Due to an unknown cause it started exibiting nasty behaviour filling up logs with the same error repeatedly. Last night we did a complete reinstall, before applying the recommended updates the system seemed fine and then after applying all recommended updates the problem started again so it seems its related to an update since the Ubuntu install ISO image. Other odd behaviour is that video doesn't playback smoothly full screen from web sites such as youtube, dailymotion etc...
The errors look like this:

Mar 19 22:14:04 tomy-linux kernel: [ 872.900268] IRQ_DISABLED set
Mar 19 22:14:04 tomy-linux kernel: [ 872.900274] irq 147, desc: c049e700, depth: 1, count: 0, unhandled: 0
Mar 19 22:14:04 tomy-linux kernel: [ 872.900276] ->handle_irq(): c01771c0, handle_bad_irq+0x0/0x2a0
Mar 19 22:14:04 tomy-linux kernel: [ 872.900280] ->chip(): c0475080, no_irq_chip+0x0/0x40
Mar 19 22:14:04 tomy-linux kernel: [ 872.900283] ->action(): 00000000

I couldn't find any useful info googling for these, can anyone help? If we can't fix this the only other thing I can really suggest my friend is try another distro, but he is quite happy with Ubuntu apart from this :S

thanks a lot, Andy.

---

