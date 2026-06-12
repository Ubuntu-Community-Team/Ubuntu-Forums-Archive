---
title: "How to restart USB Internal Card Reader?"
date: 2012-12-28
forum: Hardware
---

### Post by mechgt on 2012-12-28
Ubuntu 12.04:
I have an internal USB card reader (reads SD, compact flash, etc.).  When I 'Safely Remove Device' to unmount my SD card, it dumps the entire card reader, not just the SD card.  How do I remount/restart/reconnect/etc the internal card reader without having to reboot the entire computer?

I've read I can 'eject' instead of 'safely remove device' however I get squirrely behavior from this (card unmounts, then immediately re-mounts, or doesn't unmount at all) and just want to know how to get my card reader back once it's disconnected itself.

lsusb reports it like this:
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S

---

### Post by gordintoronto on 2012-12-28
Perhaps you could clarify what you mean by, "it dumps the entire card reader"?

Do you mean that if you insert a different SD card, it doesn't appear?

In some ways, devices which do not contain media are invisible in Linux.

---

### Post by iMac71 on 2012-12-28
> **mechgt said:**
> Ubuntu 12.04:
I have an internal USB card reader (reads SD, compact flash, etc.).  When I 'Safely Remove Device' to unmount my SD card, it dumps the entire card reader, not just the SD card.  How do I remount/restart/reconnect/etc the internal card reader without having to reboot the entire computer?

I've read I can 'eject' instead of 'safely remove device' however I get squirrely behavior from this (card unmounts, then immediately re-mounts, or doesn't unmount at all) and just want to know how to get my card reader back once it's disconnected itself.

lsusb reports it like this:
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/SPerhaps the following thread might help you:
[http://en.usenet.digipedia.org/thread/19131/64670/](http://en.usenet.digipedia.org/thread/19131/64670/)

---

### Post by mechgt on 2012-12-29
> **gordintoronto said:**
> Perhaps you could clarify what you mean by, "it dumps the entire card reader"?

Do you mean that if you insert a different SD card, it doesn't appear?

In some ways, devices which do not contain media are invisible in Linux.

By 'dumps the entire card reader', I mean it's the equivalent of ejecting/shutting down/stopping (not sure of the correct word here) the entire USB card reader (not just the SD card for example).  

This is similar to when you "safely remove" a usb flash drive... it's still physically plugged in, however the OS has stopped talking to it and it's not accessible until you physically unplug it and plug it back in.  That's what's happening to my card reader, when I believe it should only be happening to my SD card.

I cannot physically unplug and plug back in the usb card reader (connection is internal somewhere), so my only option is to reboot the computer.

If I plug in a new card, nothing happens.  The green activity light on the card reader (which is typically lit), does not light up acknowledging a card was inserted.

Any way to "unplug" and "plug back in" the card reader via a terminal command (or whatever is necessary to restart the card reader)?

---

### Post by gordintoronto on 2012-12-30
Google turned up a number of possibilities. Post 4 of this thread:
[http://ubuntuforums.org/showthread.php?t=1878064](http://ubuntuforums.org/showthread.php?t=1878064)

seemed to be a possibility. Another was changing a BIOS setting, to NOT make the card reader use a 'power saving' mode.

I suspect the command you want exists, but I don't know how to discover it.

---

