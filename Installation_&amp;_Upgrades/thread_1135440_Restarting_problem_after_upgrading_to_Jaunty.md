---
title: "Restarting problem after upgrading to Jaunty"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by mnavrotnav on 2009-04-24
After restarting following an upgrade from Intrepid to Jaunty, I cannot get Ubuntu to finish booting. Instead, it shows a message that it "gave up waiting for root device."

Common problems are listed, as well as this message:

ALERT! /dev/disk/by-uuid/405fd13f-22c3-4d78-9dd3-54d27d401c5f does not exist. Dropping to a shell!

Suggestions appreciated.

---

### Post by rdoronr on 2009-04-24
Same here.
I upgraded from 8.10 to the new 9.04 release, and have the same problem.
Googling produced some advice to type "exit" at the shell prompt, but doing this just re-displays the same message again.
My platform is HP Pavillion dv6812 dual core AMD 64 bit.

---

### Post by shayanlinux on 2009-04-25
I have exactly the same problem,
I Wait for a long time for the device, no change.

HDD is not under /dev otherwise I could mount it..
that means I don't get anything when entering these commands in the ash:
ls /dev/hd*
ls /dev/sd* (I'm using SATA)
ls /dev/disk*
dmesg | grep -i ata

Any help would be appreciated a lot. Thanks

---

### Post by glantucan on 2009-04-26
Same here too. In this case I had jaunty previously installed. Updated today to last kernel:
2.6.28-11-generic

Nevertheless, I have rt-kernel also installed:
2.6.28-3-rt

When I choose the latter in grub system works normal.

Any idea?

Glantucan

---

