---
title: "Dual boot want to format other partition and leave Ubuntu"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by green_arrow on 2009-02-21
I just got my new Sony AW and couldn't stand Vista for 10 minutes so I got me a dual boot with Ubuntu 8.10. I let the GRUB recognize Vista and be in charge.

My question is: Later down the road (tomorrow probably :)) can I format the Vista partition and expect everything to be fine and dandy with Ubuntu, i.e. starting up normally and not asking me wtf is Vista at boottime...

Thanks in advance.

---

### Post by logos34 on 2009-02-21
no problem.  

But you'll have to manually remove the vista boot entry in /boot/grub/menu.lst, as well as perhaps the entry in /etc/fstab if you format it something else besides ntfs

---

