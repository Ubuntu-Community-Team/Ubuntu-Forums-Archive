---
title: "USB Ports in General"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by BitTorrentBuddha on 2006-04-30
Okay, I'm not 100% sure if this is a Linux question or not, nor am I sure I require a Linux answer or not, but even if it's not, I assume a lot of you probably know a lot about hardware in general.

So, I built my first computer back in December, and installed Ubuntu 5.10 on it right away. But, I still can't seem to get the usb working. The jumper settings on my mother board are labelled SB5V and something else that doesn't come to mind at the moment.
When setting the jumper to SB5V I get power (or so I assume considering my dell dj lights up) but lsusb produces no output and just re-prompts for a command. When set to the other setting, It receives no power and lsusb produces no output once again. Is this a Linux question? And if not, does anybody know how I can fix it any way?

---

### Post by BitTorrentBuddha on 2006-05-01
bump :-|

---

### Post by Chris Tucker on 2006-05-23
i cant be of much help, but try this:
dmesg | grep usb
and post results

---

### Post by BitTorrentBuddha on 2006-05-23
It was jumper settings lol. I fixed it a week or so ago.

---

