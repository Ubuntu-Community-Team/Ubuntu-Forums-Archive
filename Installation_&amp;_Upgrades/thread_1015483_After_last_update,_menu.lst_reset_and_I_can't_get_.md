---
title: "After last update, menu.lst reset and I can't get into windows xp"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by spikespeigel42 on 2008-12-18
Help! After my last update, grub's menu.lst got overridden and I can't boot into xp. I tried installing lilo and having it automagically do it instead, but apparently my /etc/fstab has some weird uuid numbers, for example # /dev/sda3
UUID=bf98cf31-3cee-49ae-92e4-c406ae72719d /               reiserfs notail,relatime 0       1

I have no idea what to do!

---

### Post by joesnose on 2008-12-18
open terminal and type "sudo gedit /boot/grub/menu.lst" at the bottom of the list mine has:

title		XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

add that to your list and save.

IMPORTANT!

make sure that hd0,0 is replaced with the drive and partition you have your windows install at!!!

---

### Post by zvacet on 2008-12-19
@ **spikespeigel42**

> my /etc/fstab has some weird uuid numbers

```
sudo blkid
```

and you will see all your UUID numbers.One you will see runing above command are right,so replace one in fstab with one you get from blkid.

---

