---
title: "Help - dell 1545 partition order"
date: 2010-10-06
forum: Hardware
---

### Post by samjam on 2010-10-06
I believe that fdisk (or something like it) re-orderd my partitions and nw windows won't boot.

Can anyone with a Dell Inspiron 1545 please use 
sfdisk -l /dev/sda

and post the output so I can check the order of the diagnostics, recovery and windows partitions.

Thanks

(It happened while juggling with grub and grub-pc to try and get dual boot without windows trashing the nbr and breaking grub-pc. I got that working but bust my windows booting - and I don't have a recovery disk and my recovery partition won't boot!)

---

### Post by samjam on 2010-10-07
Some progress

Well... I got windows working by copying bootmgr from somewhere in windows\boot to the root directory - so thats fine.


However I can't get the recovery partition to boot. I managed to make the recovery DVD, but that won't boot either, for the same reason - presumably it's a bad DVD. 

I don't know what files are missing, so please could somebody post a list of the files in the root of their recovery partition?

In the meantime I'll try and knock one up with the aid of bootmgr and made it launch the recovery program along the lines of the autorun.inf file

---

