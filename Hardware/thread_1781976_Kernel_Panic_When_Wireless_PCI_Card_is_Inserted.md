---
title: "Kernel Panic When Wireless PCI Card is Inserted"
date: 2011-06-14
forum: Hardware
---

### Post by lovelypecs on 2011-06-14
Hey! So I've done a bunch of searching the forum and the web and can't find any definitive answer to what's happening here.

I have a D-link DWA 525 wireless n150 pci card. I haven't been using it lately as it is quite difficult to get the open source drivers working. But I decided to try it out once more and managed to get it working on Elementary OS Jupiter (64bit)! And the card works on my Windows XP partition.

So I decided to go ahead and get it to work with my Natty install. But when the card is in the pci slot Natty will not get past the boot splash, it just hangs on the aubergine screen. But it boots up just fine when it's not in the pci slot.

I made a live usb drive of Natty and that boots with the card inserted.

with nosplash added to the boot options I get this message and then it hangs:

```
[15.584923] kernel panic - not syncing: Fatal exception in interupt
[15.######] Pid: 942, comm: wpa_supplicant Tainted: P        D   W 2.6.38-8-generic #42-ubuntu
[15.######] Call Trace:
[15.######] <IRQ> [<ffffffff815bfece>] ? panic+0x91/0x19c

a bunch of other stuff till the last entry:
[15.######] [<ffffffff81053889>] ? wake_affine+0x149/0x320
```I also tried adding irqpoll to the boot options but that didn't work.

Any help would be greatly appreciated! And I'm willing to find more information for you if needed!

---

### Post by lovelypecs on 2011-06-15
Fixed it!

Basically I noticed some more info during the boot process and ndiswrapper was mentioned several times. Apparently I hadn't disabled the ndiswrapper drivers from previous attempts to get the card working :-/ So it was causing a major conflict and making the kernel panic when it then tried to load the open source drivers I just installed. So I simply removed ndiswrapper from synaptic and then did a file search for ndiswrapper and deleted all the residual files. Everything works just dandy now, I even have my wireless card in full working order.

---

