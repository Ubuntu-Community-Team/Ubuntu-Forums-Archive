---
title: "My card reader doesn't work in 13.04"
date: 2013-04-26
forum: Hardware
---

### Post by cdysthe on 2013-04-26
Hi,

My Lenovo L520 laptop has a Realtek RTS5209 PCI Express Card Reader (rev 01) built in. I have been able to use it without problems since I got the laptop. It runs and have been running Ubuntu exclusively. However, after I updated to 13.04 the card reader no longer works. When I insert a card nothing shows up in Nautllus and get this in the syslog:

Apr 25 21:50:03 ThinkPadL520 kernel: [94589.845738] mmc0: error -110 whilst initialising SD card
Apr 25 21:50:04 ThinkPadL520 kernel: [94591.005193] mmc0: error -110 whilst initialising SD card
Apr 25 21:50:05 ThinkPadL520 kernel: [94592.260475] mmc0: error -110 whilst initialising SD card

The card works fine in my camera and in other computers so it's nothing wrong with it. Its a 8 GB Trancend Micro SD HC (with adapter). Any idea what may be wrong? Seems to me the kernel and  driver for this card reader has problems, but I'm no expert at all so I was hoping someone here could point me in the right direction.

---

