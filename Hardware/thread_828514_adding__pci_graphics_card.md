---
title: "adding  pci graphics card"
date: 2008-06-13
forum: Hardware
---

### Post by smw3692 on 2008-06-13
I have a compaq presario that I bought in 2000. It has an intel on board graphics card {an 810} I have tried to add a nvidia PCI card in the past. I go to bios, disable My onboard card but Ubuntu still recognizes and configures the on board card as all live distros do I would like to boot up in text mode and issue some sort of command to have Ubuntu at least give Me a choice as to what card to configure. Is there anyway to do this? Would an ATI card work better?

TIA 
Steve

---

### Post by pytheas22 on 2008-06-13
If the onboard card is disabled in BIOS, Ubuntu shouldn't even be able to see it to configure it; it should be like the card doesn't exist.  Make sure it's definitely disabled.  There may also be an option in BIOS where you can specify which card will be the primary one; make sure the PCI card is first.

Also do you have just a regular PCI card, not PCI express?  Because if so, the problem could lie there, as your BIOS might think that video cards can only exist on the AGP or PCIe buses.  So when it doesn't see any in those places, it keeps the onboard card enabled.  I had a machine with this issue once.

Regular PCI is bad for graphics cards anyway because it's just too slow.  Even if your card is really good, you probably won't get performance much better than that of the i810, because the speed of the PCI bus is too slow.

---

### Post by DirtDawg on 2008-06-13
I just replaced my onboard i810 a few weeks ago with a new PCI card. My research suggested that when I installed the PCI card, the onboard card was disabled automatically. I think you actually need to install software and do some tweaking to get both running (ie: dual screen).

To pytheas22: I have to say, my PCI card outperforms the i810 drivers by leaps and bounds. The intel drivers for Linux are absolutely *terrible*.

---

### Post by pytheas22 on 2008-06-13
> The intel drivers for Linux are absolutely terrible.

Just on a side-note to the real thread: I'm very happy with my integrated Intel 945 graphics, and Intel is probably the most open-source friendly when it comes to graphics cards.  No one else releases completely free drivers.  I have had a few issues in earlier versions of Ubuntu, but in Hardy the video is really fast and stable.  I don't want to join the ranks of all the people who post so many threads about not being able to get their nvidia or ATI cards working properly, and often running into the answer that (especially with nvidia) the drivers are closed-source and there's nothing that can be done besides wait for nvidia to decide to fix the problem.

Of course, the downside of Intel cards is that they are not made for spectacular performance, so if you need to do gaming and things, obviously Intel is not going to cut it for you.

---

### Post by smw3692 on 2008-06-14
Thanks for Your replies..I don't intend to play games or anything sometimes I just come across a graphically intense web page that appears really jumpy so I don't think it is worth the trouble to add a card

Thanks again

Steve

---

