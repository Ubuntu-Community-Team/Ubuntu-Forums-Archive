---
title: "usb keyboard is like thiiiiiis, reset in dmesg"
date: 2008-11-20
forum: Hardware
---

### Post by eteq on 2008-11-20
I've been encountering an odd problem in Interpid (it was present in Hardy, also) on my Asus F8Sv laptop.  I have an Asus-branded USB mouse and a Microsoft keyboard that I connect when I'm using my laptop in the office, and while they work fine when I connect them directly to the laptop USB ports, if I connect them to my Apple cinema display (which has a built-in hub), I get continuous dmesg entries that look like 

"reset low speed USB device using ohci_hcd and address #"

and the keyboard works erratically, leaving text that looooooks liiiiiike thhhhhhis or doesn't work at all (or the keyboard works fine and the mouse doesn't work at all).  Curiously, if I have just the mouse, or just the keyboard plugged in on any of the ports, they work fine, but when both are plugged into the cinema display, whichever is on the leftmost port gives the problem.  

I also tried using a co-worker's keyboard (using right now), and it works just fine.  Now, I admit that I'm asking for trouble routing a microsoft keyboard through an apple cinema display into an asus laptop running Linux, but it does work perfectly fine in Vista... so it's some combination of linux and the hardware that's the cause of the problem.  Any ideas?

---

