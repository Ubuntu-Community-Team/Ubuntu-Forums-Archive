---
title: "Wireless on EEEPC 901"
date: 2011-05-10
forum: Hardware
---

### Post by martinjh99 on 2011-05-10
This is the wireless chipset I have in my little netbook:

```

 *-network
       description: Wireless interface
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:e5:47:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:f7ff0000-f7ffffff

```

 I am running the following kubuntu kernel:

```
Linux alice 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
```

Im trying to connect to a Linksys router that has been flashed with the tomato firmware and has a WPA2 Personal password set.

Am having not much luck - it hangs at configuring network stage according to the network icon.

It has been working before when i installed - but it dropped the connection for some reason and haasn't really been working since!

I have done the blacklisting of some of the modules that i found on the internet but that doesn't work either so what can i do about it..?

---

