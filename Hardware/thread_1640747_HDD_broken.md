---
title: "HDD broken?"
date: 2010-12-08
forum: Hardware
---

### Post by rabby_ on 2010-12-08
Hi,

Today I switched into tty1 and found a worse error message:
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata1.00: failed command: READ DMA
ata1.00: cmd ... tag 0 dma 4096
ata1.00: status: { DRDY }

Sounds like a inconsistent hdd, so i had a look at
smartctl -lerror /dev/sda
which says:
> smartctl -lerror /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
No Errors Logged

OK, no error, but what is the reason for this error message?

The machine has only /dev/sda as hdd with several partitions, so if there was an error, my root partition would be in danger, too :-(

Thanks for help.

PS: Some days ago, ubuntu failed with the hdd check on boot. After fsck from rescue disk the issues seemed to be solved an fsck (again) said "no error". Is it a good idea to go on with this device or better idea to replace it before losing data?

---

### Post by dandnsmith on 2010-12-08
I'd put a new HDD on ASAP - especially if you want a chance at saving some stuff from the existing one.

---

### Post by rabby_ on 2010-12-08
I mirror the data since i know about the hdd having troubles...
However, restarting again did not show up any errors, fsck does not tell a notice, warning or error. Same result with smartctrl.
Won't any of these tools return results or provide a chance to fix this? I mean... how to trust this hdd again if i can not even detect errors when re-checking?

---

