---
title: "Can't get HP Parallel printer to work"
date: 2011-07-29
forum: Hardware
---

### Post by technoboi on 2011-07-29
Running Ubuntu 11.04 Classic. Fully updated.

Firstly: The printer and cable are perfectly OK.

I have a HP 820cxi Deskjet parallel printer.
I upgraded my computer and had to add a parallel printer card as there was no suitable provision on the new motherboard.

I have read many posts and have tried all that I have read.

After first booting and going to System/Administration/Printing > 'Add' it will briefly show LPT#1. Cancel the 'Add' and go back again and it no longer appears. When it does occur it does no better install than if I do it via 'other'. Lp0 exists in /dev. So I select 'Other' and set 'device URI' to parallel:/dev/lp0. I have tried the database route from there. I also have tried adding a ppd file. To get that to work, without throwing an error, I had to edit /etc/cups/cupsd.conf

I get the usual message asking if I want to print a test page but nothing happens after that.

lspci doesn't bring up a printer card so I suppose it is not going to 'fly' anyway.

In dmesg the only possible reference is:
'ppdev: user-space parallel port driver'
No relevant error messages etc are present.

I suppose that the printer card could be faulty, but, failing that, has anyone any ideas please?

---

