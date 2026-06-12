---
title: "How to diagnose SD card problems?"
date: 2011-08-01
forum: Hardware
---

### Post by Jinren on 2011-08-01
Hey all,

I have an ancient eeePC 701, that's stopped recognising the SD card for some reason.

Previously the card would automatically mount when inserted and generally be usable as one would expect. At some point, and importantly I don't know when or what I may have done, it stopped. Now inserting or removing a card does nothing. The card I'm using works fine on my other computers, and worked before, so I don't expect that's the problem.

Attempting to mount the device using "sudo mount /dev/sdb1 /mnt" freezes up (is this right? I don't actually know anything about this!).

"lspci | grep Card" return nothing.

I can find the device using Device Manager (gnome-device-manager), now that I know where to look; one of the four entries for USB controllers mentions the word "CardReader" on the properties page, so I suppose that's it, but the tree view on the left just calls it a generic interface.

"dmesg" prints out a lot of stuff I don't understand at all, but what looks relevant is a lot of repeated mention of "Buffer I/O error on device sdb", and similar things.

I tried reinstalling the operating system (unfortunately I don't know how to do more subtle maintenance than that yet), which had no effect.

...is the cardreader somehow broken? If so, how can I tell? Anyone got any suggestions for ways to get more information, or possible fixes?

Thank you for reading!

---

### Post by Jinren on 2011-08-03
Turns out I had disabled something in the BIOS, so nothing to do with Ubuntu whatsoever. Solved, I guess?

---

