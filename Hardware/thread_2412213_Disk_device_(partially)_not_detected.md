---
title: "Disk device (partially) not detected"
date: 2019-02-09
forum: Hardware
---

### Post by meliniak on 2019-02-09
It all started when my laptop begun to randomly restart, probably due to some battery issues.


Now, when booting from grub, it fails and says:


ALERT! UUID=(uuid value) does not exist. Dropping to a shell
The uuid is the root value in linux command in grub.


Other symptoms are as follows:



[LIST]
[*]When booting from LiveCd, there is no disk device under /dev/
[*]The disk and my Ubuntu partition can be accessed from grub shell (the one which is entered by editing a grub entry), so clearly the disk still works
[*]Windows on another partition works fine
[/LIST]

This issue should be easily repairable, if only the disk device was there when booting from LiveCD. Any hints what can be done in this case?

---

