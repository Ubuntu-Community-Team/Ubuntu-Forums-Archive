---
title: "Can't Access Secondary HDD"
date: 2016-10-17
forum: Hardware
---

### Post by jaws92 on 2016-10-17
I recently deleted Windows from my primary drive and installed Ubunutu. I have a lot of files on my secondary drive, but when I click it nothing happens. 

If I try to mount it, I get the following message:

 [IMG]http://i.imgur.com/izOXXXI.png[/IMG]

How can I gain read/write access to it?

---

### Post by jaws92 on 2016-10-17
I found the answer on another thread.

Type: "[COLOR=#333333][FONT=Ubuntu]Solution: type "sudo ntfsfix /dev/sdXY" into terminal, where X is the drive and Y is the partition.

Example: [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"sudo ntfsfix /dev/sda1" [/FONT][/COLOR]

---

### Post by ajgreeny on 2016-10-17
I suspect that the partition on the secondary drive was still flagged as in use (possibly hibernated?) which is the default shutdown state of partitions in Windows 8, 8.1 and 10, but I'm not sure about Windows 7.

How did you remove Windows?
Did you use fast start in Windows? That is the hibernation state I mentioned.
Do you have another Windows machine that you can attach the disk to in order to properly shutdown the filesystem on it?

EDIT:
I see you found and posted a solution while I was still replying, so please now mark as solved from the Thread Tools menu up top.
It is very helpful to users searching the forum.

---

