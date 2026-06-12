---
title: "Wipe HDD"
date: 2017-02-02
forum: Hardware
---

### Post by vall1986 on 2017-02-02
I wiped HDD by command ```
[COLOR=#333333][FONT=ubuntu]dd if=/dev/zero of=/dev/sda bs=512[/FONT][/COLOR]
``` to remove grub from disc. But now when I want to create new partition table I have GParted warning: [COLOR=#333333][FONT=ubuntu]"The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.". I've tried [/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]dd if=/dev/zero of=/dev/sdX bs=2048 count=1[/FONT][/COLOR]
``` bud it didn't help. Any idea what to do about it, please?

---

### Post by geeksmith on 2017-02-02
Have you tried using another tool, perhaps fdisk or cfdisk, to create a new partition table?

---

### Post by vall1986 on 2017-02-02
No, I will try.

---

### Post by vall1986 on 2017-02-04
I made partition table and new partitions in fdisk but it didn't remove gparted warning. So I ignored this warning and made finally partitions in gparted. It works, I hope there won't be any problem.

---

