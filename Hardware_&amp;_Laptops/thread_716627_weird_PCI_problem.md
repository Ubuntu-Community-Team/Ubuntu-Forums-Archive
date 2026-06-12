---
title: "weird PCI problem"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by ppw0 on 2008-03-06
First I'd like to say hi to everyone on this forum :)

I have two PCI cards, one is a Realtek 8139 ethernet controller (LevelOne) card, and the other one is a Ralink RT61 (D-Link DWL-G510) wireless network controller card. The weird problem is that whether or not the cards get recognized by the Ubuntu installer is dependent upon where they are inserted. If either of them are inserted into the very first PCI slot, they just don't get detected, otherwise they do. There is no entry in the lspci output at the Ubuntu text mode install, and afterwards, the installer complains that there are no network interfaces to be found (you could imagine the look on my face after seeing that yet knowing the Realtek card and LAN cable is plugged in).  And because those two cards are the only ones I've tried, I assume no PCI card would get detected if it were inserted there. This happens with every installer image I've tried (Gutsy netboot, Hardy netboot, and Gutsy official Live CD). I've also tried booting with options pci=routeirq and pci=assign-busses, but it didn't work.
I *think* the same problem was present in Windows, but I didn't even notice it (there were many problems there which were much worse, and after 15 minutes of hassle that I couldn't stand, Ubuntu was the way to go ;-)). Ubuntu installed fine however. I just used the Gutsy official Live CD to install it, switched the cards around as to get the network controller working, and downloaded the necessary updates. But the first PCI slot is still a no-go.

The motherboard is an old K7S5A (v3.1). There's also a USB controller plugged in with 4 USB ports, and that's it for the PCI slots. Otherwise, there's an old ATI AGP card inserted into the AGP slot as well.

So why does that occur? Any suggestions?

Thanks

---

### Post by teaker1s on 2008-03-12
stupid question but, the slot is the same colour? reason I ask is that a couple of boards I came across had an option to plug in a manufacturers adapter and a bios setting to make the slot only for this?

---

### Post by ppw0 on 2008-03-12
Yeah, sure, as you can see here

[http://sgj.fm.interia.pl/k7s5al/k7s5a-b.jpg](http://sgj.fm.interia.pl/k7s5al/k7s5a-b.jpg)

all PCI slots are white. I think there are some options in the BIOS to disable certain PCI slots, but I think they're all set to "Auto" and you cannot make any changes.

---

### Post by ppw0 on 2008-05-28
Guys? Help? :(

---

