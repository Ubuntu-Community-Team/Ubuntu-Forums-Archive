---
title: "Installing ATA controller makes ubuntu=unbootu"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by [CTG]ChAoS Overlord on 2005-06-15
Hi,

I was planning to add an extra IDE drive to my ubuntu server, but since I have no free ATA channels I added a Silicon Image 680 card.

As soon as I pop in this card, ubuntu doesn't boot anymore. The card itself is in perfect working order, since I can get it to work on my windows machines.

I haven't modified my ubuntu except for the kernel I'm running, it's the "linux-k7" kernel, since I'm using a duron 1200 MHz CPU.

The error is like this:

> starting ubuntu...
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel Panic: - Not syncing: attempted to kill init!

When I remove the controller, it boots perfectly again.

---

### Post by [CTG]ChAoS Overlord on 2005-06-15
I tried booting with the default kernel (386) and the recovery modes: same error.

---

### Post by TheCondor on 2005-06-15
[QUOTE='[CTG]ChAoS Overlord']Hi,

I was planning to add an extra IDE drive to my ubuntu server, but since I have no free ATA channels I added a Silicon Image 680 card.

As soon as I pop in this card, ubuntu doesn't boot anymore. The card itself is in perfect working order, since I can get it to work on my windows machines.

I haven't modified my ubuntu except for the kernel I'm running, it's the "linux-k7" kernel, since I'm using a duron 1200 MHz CPU.

The error is like this:



When I remove the controller, it boots perfectly again.[/QUOTE]


I get the exact same error when booting with my own compiled kernel that had support for the silicon image 3114 sata controller ! I havent found a solution to it yet, I thought the kernel compilation was done correctly but it seems somethings wrong  ](*,)

---

