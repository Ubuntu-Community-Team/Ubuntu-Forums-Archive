---
title: "Unloading ndiswrapper for standby and hibernate"
date: 2009-05-27
forum: Hardware
---

### Post by networkproblems on 2009-05-27
I have a Quanta KN1 laptop with a Belkin wireless card plugged into my PCMCIA slot, and my only option for a driver was a windows one running on ndiswrapper. When I suspend/standby the computer and then resume, I have to unplug the card and then plug it back in to connect to wireless. Also when I try to hibernate/sleep and the memory starts to cache to the hard disk, I get a ndiswrapper error that says it can't find my driver. 

Is there a way to automatically stop ndiswrapper before hibernate and standby? I also need to automatically restart it when I resume from both. If there is a better way than unloading ndiswrapper, then it's welcome.

I've already installed uswsusp, hibernate, and tuxonice. None of them are making it work.

Setup: Ubuntu 9.04 x86, Intel 915GM graphics, Airgo networks AGN100 True MIMO a/b/g wireless card

Thanks

Edit: Ok, I gave up and just ordered an internal wireless card that's supported by linux. The belkin card got too hot anyway.

---

