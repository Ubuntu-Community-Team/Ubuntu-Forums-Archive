---
title: "Card Reader Ricoh R5C822 not working on Asus A8Jn (Fiesty 7.04, 2.6.20-16 kernel)"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by maple03 on 2007-05-30
Card Reader doesn't work on my Asus A8jn laptop. I'm running Fiesty 7.04, 2.6.20-16-generic kernel. This is is what I get:

lspci:
06:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:00.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
lspci -v:
06:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
Subsystem: ASUSTeK Computer Inc. Unknown device 1447
Flags: bus master, medium devsel, latency 64, IRQ 22
Memory at feaff400 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2

06:00.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
Subsystem: ASUSTeK Computer Inc. Unknown device 1447
Flags: bus master, medium devsel, latency 0, IRQ 5
Memory at feaff000 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2

06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
Subsystem: ASUSTeK Computer Inc. Unknown device 1447
Flags: medium devsel, IRQ 5
Memory at feafec00 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2

06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
Subsystem: ASUSTeK Computer Inc. Unknown device 1447
Flags: medium devsel, IRQ 5
Memory at feafe800 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2


# lsmod |egrep '(sdhci|mmc)'
mmc_block 13832 0
sdhci 18700 0
mmc_core 26756 2 mmc_block,sdhci

# ls /dev/mmc*
ls: /dev/mmc*: No such file or directory

**And nothing in dmesg when I insert a MMC-card. I tried to boot with the card inserted, but that gave no results too. Can someone help me?**

---

### Post by maple03 on 2007-05-31
Well, I know, that drivers are supposed to be included in kernel since 2.6.17, but nothing is working. Can anyone help me, or give some advices where to search?

---

### Post by dizm on 2007-06-01
I have what may be the exact same problem, same device. with feisty on a dell inspiron 9400.

I just tried `sudo modprobe tifm_sd` (ref: [http://www.arsgeek.com/?p=1556](http://www.arsgeek.com/?p=1556))

let's see...

---

### Post by dizm on 2007-06-01
this seems like the story: [http://tuxmobil.org/mmc_sd_card_unix.html](http://tuxmobil.org/mmc_sd_card_unix.html)

---

### Post by rhodry on 2007-06-01
> **dizm said:**
> I have what may be the exact same problem, same device. with feisty on a dell inspiron 9400.

I just tried `sudo modprobe tifm_sd` (ref: [http://www.arsgeek.com/?p=1556](http://www.arsgeek.com/?p=1556))

let's see...
Worked like a treat on my Asus A6Jc!

'Kodak' icon on the desktop, gThumb pops up and offers to import photos direct to library. Don't forget to unmount before removing though.

This is much easier than mucking about with usb cables, especially when my hub is full.

 How I LOVE these forums!

---

### Post by mezhaka on 2008-01-05
hello,

i got the SD card running as suggested at [http://www.arsgeek.com/?p=1556]("http://www.arsgeek.com/?p=1556"), but the memory stick does not work still. has anyone succeded with memory stick?

---

