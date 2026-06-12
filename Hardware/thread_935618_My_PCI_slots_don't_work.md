---
title: "My PCI slots don't work"
date: 2008-10-01
forum: Hardware
---

### Post by shaggy999 on 2008-10-01
Ok, at this point I've determined this is NOT a Linux problem but a hardware problem in general. I'm hoping someone can help me figure this out, though.

I just bought a used PIII system that I was told was working fine. This machine is an upgrade from my current PII 333Mhz system which I'm typing on right now in elinks. :( The problem is I needed to plug a wireless card into it to get an internet connection. But the device doesn't pop up at all! When I run the lspci command it doesn't show up at all.  I finally noticed that when first booting the BIOS starts up it shows a list of conected PCI devices. But the only PCI devices it shows are the onboard devices!

The motherboard has two PCI slots and I've tried the card in both of them. The motherboard is a "PC Chips M756T+ series" motherboard and the wireless card works perfectly fine in my older machine (which I'm using now to connect to the internet).

Another weird error is that if I trty to plug a second hard drive into the system the power supply blows (it lasts about 3 seconds before it shuts itself off and I have to disconnect the power supply from the motherboard and then reconnect it before it will power on again.

Things I've considered:

1) Bad BIOS - Perhaps there's a BIOS issue and there's a fix for it, but I can't seem to connect to the PC chips website at the moment.

2) Power supply issue? One possibility is that maybe the power supply can't power the PCI slots? I only thought this since it has trouble with a second hard drive (although the power supply is 300W which is 50W more than my older computer which has 4 hard drives in it!)

3) BIOS setting - The only setting I could find was a "PCI SLOTS" option which has 4 options - Both, Primary, Secondary, and Disabled. I have it set to Both.

4) The motherboard is just toast.

I should also mention that I've tried plugging in 2 other network cards (not wireless, just ethernet) and they won't work either.

Any ideas?

---

### Post by coolbrook on 2008-11-08
I'm experiencing the same problem on one of my systems (Intel D850MV.)  I thought it was a bad sound card on my PCI slot, but Ubuntu also isn't detecting the wireless adapter (WG311T) I just installed in another.  Unfortunately I don't have anything relevant to configure in my BIOS.

---

