---
title: "Kubuntu 8.10 freezes within 1 hour after boot"
date: 2009-08-25
forum: Hardware
---

### Post by skatebiker on 2009-08-25
Since a week my Kubuntu 8.10 freezes mostly within an hour after boot.
I did not install any new hard or software other than normal OS updates.
I read in several forums about an HPET timer which can be disabled by the following line in /boot/grub/menu.lst:

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=70f4a30b-4f95-445b-91eb-4ccf9a77fac3 ro quiet splash hpet=disable

but that does not help.
It is not a memory problem as the memory test boot option of Ubuntu does not show any errors and Windows Vista boots normally.

Hardware: Sony VAIO VGN-FZ21M with 2GB of memory.

Is there any solution for this ?

---

