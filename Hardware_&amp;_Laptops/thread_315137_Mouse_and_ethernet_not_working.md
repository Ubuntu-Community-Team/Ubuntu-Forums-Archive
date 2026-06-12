---
title: "Mouse and ethernet not working"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by efreddi on 2006-12-08
Hi All,

yesterday evening I tried to set up the Agere LT WinModem that I have on my laptop (Dell latitude C600) on the same PCI board of the Ethernet (Intel Pro 100). I followed the instruction given at this link [DialupModemHowto/Lucent]("https://help.ubuntu.com/community/DialupModemHowto/Lucent")

After rebooting the mouse is frozen (a generic PS2 mouse), the ethernet is not working and of course the modem isn't alive!

This is the output of ***lshw -C network***:

[I]-network UNCLAIMED
      description: Ethernet controller
      product: 82557/8/9 [Ethernet Pro 100]
      vendor: Intel Corporation
      physical id: 10
      bus info: pci@00:10.0
      version: 0c
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list
      resources: iomemory: f3ffd000-f3ffdfff ioport: dc80-dcbf iomemory f3fc0000-f3fdffff irq:11[/I]

No idea how to get a similar output for the mouse.
I tried already to restore the files before the changes for the trial of the modem, but no way. No answer from the command ***ifconfig -a*** for the ethernet card.
I tried the liveCD and everything works, so I exclude hardware issue.

Any suggestion is welcome! Thank you!



Elia Freddi

---

### Post by efreddi on 2006-12-12
I solved the problem reinstalling the whole system using the alternate install disk. Ok, it's not a solution but in 10 minutes the system was back on the way.



Elia Freddi

---

