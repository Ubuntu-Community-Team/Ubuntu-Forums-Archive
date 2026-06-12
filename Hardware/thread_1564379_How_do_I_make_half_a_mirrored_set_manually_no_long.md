---
title: "How do I make half a mirrored set manually no longer a mirror?"
date: 2010-08-30
forum: Hardware
---

### Post by runatyr on 2010-08-30
Hello and thank you to anyone that reads this.

History:
I own an Iomega NAS enclosure. It is basically a card with 2 sata drives attached and a network card that runs an small web interface.

To make a long story short. The controller card has went bad.
One drive dropped out of the mirrored set.... and then came back in and attempted to rebuild. Several hours later the drive dropped out again.
I attempted to replace the drive and the controller would not rebuild at all.

To summarize. I have accepted that the controller card is toast and want to proceed assuming one drive is compromised and the other still has salvageable data (About 18 GB needs recovered)


I took the presumed "good" drive.. attached it to a standalone enclousre that takes it from sata to USB.

When I look under disk manager (using Ubuntu 10) I see the following appear
1) the multi Disk device appears indicating it is part of a logical drive. Indented from that is
2) The "Array" Icon
3) The USB icon indicating a "peripheral device"
Indented from that is
4) the Drive as a 500 GB hard disk (correct)

when i click on 4) I see 2 volumes 1 1GB volume with partition type Linux (0x83) and a 499 GB partition with the same type (0x83)

However..because it thinks it is part of an array it is not mounting...

So... HOW do I tell this drive "you are not in an mirrored array anymore...mount as a single drive"

any advice is appreciated.. Again..thank you for your time

---

