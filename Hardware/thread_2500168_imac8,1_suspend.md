---
title: "imac8,1 suspend"
date: 2024-08-24
forum: Hardware
---

### Post by snowcrash1 on 2024-08-24
I just installed Ubuntu 24.0.1 LTS on my iMac8.1 and everything works!  Good News!  (My scanner doesn't, suspend doesn't)  Umm, its a Smashing Success!  Networking works after updating online and +upgrade with WAN.  Video started working, zoom, scribus.  I'm attaching the lspci document I got.  [https://pastebin.com/zrfTS6Bs](https://pastebin.com/zrfTS6Bs)  These are my specifications, and most everything is able to function.  Still a few bugs when I open too many windows, it becomes unresponsive happened once (I had five or six programs that were competing).  Otherwise, I highly recommending repatriotating old iMacs.  Runs like a champ!

Five Minutes to Boot

Suspend is funky.

What can I do about it?  Suspend returns blanched, has something to do with acpi so I put this into my grub file:
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=SHOW
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="ro acpi_osi=Linux  vbeinfo"

I'm thinking that when it suspends, it defaults to the lowest common denominator.  And acpi inherits those settings?  Loads from the bottom?
As a result of these settings, my screen gets grayed out AFTER SUSPEND

How can I fix suspend or my epson scanner?

---

