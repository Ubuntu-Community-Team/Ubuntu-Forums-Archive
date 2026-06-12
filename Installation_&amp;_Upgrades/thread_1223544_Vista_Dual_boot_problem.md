---
title: "Vista Dual boot problem"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by drlinux on 2009-07-26
Can anyone help me.

Setting up a new system as below:

Intel core 2 Duo E 8500 CPU GA EP45UD3R Motherboard 2 G DDR II RAM
2x 750Gb Power SATA II HDD
1 G Geforce GTX 285 PCI Express

Software:
Window Vista Home Premium

Vista sits on one hard drive – Sdb1
2nd Hard Drive has the following partitions;
Sda1 FAT 32 100Gb for shared files with Linux and Windows
Sda2 Linux Ubuntu


I added this to the Grub menu.lst file:

title Microsoft Windows Vista
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
savedefault
makeactive
chainloader +1

When I select Vista off this list I get the message

"BOOTMGR is missing"

Can you help me with this one?

---

### Post by merlinus on 2009-07-26
Try changing this

title Microsoft Windows Vista
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
savedefault
makeactive
chainloader +1

to this

title Microsoft Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

Also check your hdd boot order in bios.

---

### Post by drlinux on 2009-07-27
Thanks for that Merlin. At work now so will try in few hrs

---

