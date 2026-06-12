---
title: "Every now and then, one random letter/number/symbol is typed by something."
date: 2011-02-21
forum: Hardware
---

### Post by sysghost on 2011-02-21
Greetings.

I got ghosts in my system... <looks at my nick> ... *umh* ... well ... it's not me this time.

Just as the title mentions, a random letter or symbol are typed every now and then. (With a few minutes interval)
At first I thought it was my keyboard or mouse that behaved strange, so I tested unplugging all my input devices (HID related ones)
No change. still a random letter/symbol is being typed from time to time.
These random letter typings does not occur under Windows, only under Linux as far as I've tested.

-"Enough!" I said and decided to go deep down with this ghost of mine.

Uplugged virtually every single hardware that isn't vital for the system. Left are: 
* ATX computer case.
* Power supply.
* Motherboard.
* CPU.
* one memory module (Usually there are four modules)
* Graphic card.
* a monitor.
* Network cable. (SSH, reading logs, etc.)

Absolutely nothing else connected, not even a single USB/PS2 device.

After some time at it (and a few bad words) I did not succeed to oust the ghost.
But I did find out, if I unload the HID kernel module, the random typing stops.
( I knew it had something to do with the HID system, but what exactly I don't know)

Strange enough, the random typing only happens within any Linux distribution.
Other kernel versions seems to make no difference. 
I also tested Gentoo, both install and liveCD, same behaviour, (Both custom kernel and genkernel )

Another thing I've noticed during test:
This problem seems to be within the motherboard.
If I change the motherboard, the problem goes away with it.
Putting the motherboard in another system, different hardware, the problem reappears.

I also had this problem with another system recently, differend motherboard model, but almost the same chipset:

Motherboards (Chipsets) in question:
* Asus M3A32-MVP Deluxe (AMD 790FX/SB600)
* Asus M4A79 Deluxe (AMD 790FX / SB750)

I suspect the SB600/SB750 SouthBridge chips being responsible for my "keyboard ghosts". ( USB system? )

My questions are:
How can I track details and read debugging within the HID system?
What virtual (non-physical) HID devices could cause this behaviour?
Do anyone recognise this or had a similar problem? ( if so, how was it solved? )

You find this weird?... well... so do I.

---

