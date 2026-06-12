---
title: "Default to onboard VGA instead of graphics card"
date: 2017-10-17
forum: Hardware
---

### Post by matthias-karl on 2017-10-17
Hi

I have an older PC running ubuntu 16.04.3. It runs Plex Media Server and has no keyboard or screen directly attached.

While I can access it via a remote desktop from my main PC, I still would prefer to have some sort of easy "direct" access to the machine.

I do have a wireless Logitech keyboard for which I can just switch the USB sender from my PC to the Linux machine to have the keyboard. But reconnecting the monitor cable is somewhat annoying.

My ubuntu system has a graphics card and I was thinking that Plex might benefit from this when transcoding movies while streaming them. So that's why I still have it in. 

Is it possible to keep the card for this purpose (does Plex even use it?) and still have the desktop shown on the VGA port? Then I can just hookup a second cable to my monitor and just switch the input signal as required.

Thanks in advance for your help.

---

### Post by Autodave on 2017-10-17
Simple answer is "no". Once a graphics card is added, assuming it is PCI, the on-board graphics is disabled automatically by the MOBO.  Before PCI, adding a graphics card meant removing a jumper on the MOBO to enable the graphics card to work. Once the jumper was removed, the on-board graphics ceased to function.

---

### Post by matthias-karl on 2017-10-17
Ok, thanks

---

