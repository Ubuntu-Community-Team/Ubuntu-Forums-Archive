---
title: "Dropped to Grub shell after stage 1 of installation"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by GregMartyn on 2005-12-21
Background:
I'm trying to install kubuntu's Flight-2 Dapper Drake from CD.
I have two SCSI controllers.
hd0 (grub) is sde (as seen by the install cd's kernel)
another way of saying that: I configured the bios to boot from the disk that the linux kernel on the install cd recognizes as sde. Depending which scsi card's modules get loaded first, it can either be sde or sda.

I format sde with 3 partitions: /boot, /, swap
I elect to install grub to the mbr. (It correctly puts it on sde)

After the (first, only) reboot during installation, I am dropped to a grub shell. There are no boot options. I have to enter the following manually:

kernel /vmlinuz[something] root=/dev/sde3
initrd /initrd[something]
root (hd0,2)
boot

After that it boots fine, but I don't think entering that info manually is the expected behavior.

After using Adept to upgrade my kernel, /boot/grub/menu.lst looks like it is filled incorrectly.

example:
title Utuntu kernel 2.6.15-9-386
root (hd6,0)
kernel /vmlinuz-2.6.15-9-386 root=/dev/sde3 ro quiet splash
initrd /initrd.img-2.6.15-9-386
savedefault
boot

the kernel line is correct, but the root (hd6,0) should be (hd0,0)


At no point does grub actually work correctly anyway; it completely ignores the menu.lst and makes me type this stuff in every time I boot. I just thought I'd mention the menu.lst errors too..


Are these two different bugs? Are they known? I did a quick search and didn't find them, but maybe someone else knows better than I.

Thanks.

---

