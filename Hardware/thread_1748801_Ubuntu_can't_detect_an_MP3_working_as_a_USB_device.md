---
title: "Ubuntu can't detect an MP3 working as a USB device"
date: 2011-05-03
forum: Hardware
---

### Post by GabryHyrule on 2011-05-03
Hi everyone, I'm running Ubuntu 11.04 on a new computer, this is my first time with linux.
I'm trying to connect my MP3 player, which, in windows at least, works exactly like a USB stick. Any other USB device works on my computer. I also tried it with all the ports and even with everything else unplugged. My USB's partion is FAT.

Anyways, when I use the dmesg command in the terminal, I get the following three lines, repeating every 2-3seconds:
USB 5-5: new full speed USB device using ohci_hcd and address XX
USB 5-5: can't set config #1, error -62
USB 5-5: USB disconnect, address XX

It also displays the message "hub 5-0:1.0: unable to enumerate USB device on port 5", but I'm not sure if this is related.

And my MP3 reacts accordingly, he's acting as if I was repeatedly plugging and unplugging it.

Thanks to anyone willing to help me!
If it can help, windows says my device is "IVORY SM-W51200 UMS USB".

---

### Post by GabryHyrule on 2011-05-07
legitimate bump?

---

