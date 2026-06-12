---
title: "chainloading problem"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2009-06-21
I have following configuration (GRUB notation):

(hd0,0) - WinXp
(hd0,1) - /boot/grub
(hd0,4) - ubuntu + GRUB
(hd2,0) - WinXp
(hd2,1) - ubuntu + GRUB

(hd0,1) is dedicated GRUB partition and has only /boot/grub on it, nothing more. When I boot from (hd0,4) or (hd2,1) everything is fine. But, when I try to chainload from (hd0,1) to any of these two, I get Error 13. Chainloading Windows works fine. Here is my menu.lst from (hd0,1):

-----------8<-------------

title   Kubuntu 9.04
root    (hd0,4)
chainloader     +1

title   Kubuntu 8.04
root    (hd2,1)
chainloader     +1

title           WinXP novi
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

title           WinXP stari
rootnoverify    (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

title           Direkt:
root

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            b0702c11-da08-4b18-bc13-788a57c890af
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=b0702c11-da08-4b18-bc13-788a57c890af ro quiet splash
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            b0702c11-da08-4b18-bc13-788a57c890af
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=b0702c11-da08-4b18-bc13-788a57c890af ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=32d228db-6543-423e-b68a-32f9044c9eec ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
savedefault
boot 

-----------8<-------------

So, from this list only first two entries give me "Error 13: Invalid or unsupported executable format.", everything else works fine. Any ideas why chainloading doesn't work?

---

### Post by dijxtra on 2009-06-21
Problem solved. I obviously installed GRUB to MBRs of the drives instead of boot records of partitions. So, setup (hd0,4) and setup (hd2,1) solved the problem.

---

