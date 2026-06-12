---
title: "karmic alternative cd install network hardware detection failed"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Serguei_89 on 2009-10-31
Hello,

Installing on Acer Aspire One using the alternative CD. During the hardware detection step it failed to detect network hardware. I can't install anything since I can't connect to the wired network.

What should I do to install Karmic alternative on Acer Aspire One?

---

### Post by macogw on 2009-10-31
The Alternate CD does not require a network connection to install.  Not configuring the network during install is just fine.

---

### Post by Serguei_89 on 2009-10-31
Well that's what I thought too and went ahead with the installation.

But, maybe it's because I chose to install just the "command-line system" when I booted into the new installation, ifconfig shows just the inloop. That was not what I expected.

Shouldn't "command-line system" include network ethernet drivers? 

So anyway, I did the install ignoring the lack of network detection during the install, but there was no network connection afterwards either. What do I do?

---

### Post by macogw on 2009-10-31
does ```
ifconfig -a
``` show more devices? If no, can you show the network devices listed in ```
lspci
```?

---

