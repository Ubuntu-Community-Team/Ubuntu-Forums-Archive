---
title: "Ubuntu 16.04/16.04/17.10 crashes"
date: 2017-10-23
forum: Hardware
---

### Post by oguz-189013 on 2017-10-23
I have an ASUS X555B with AMD Radeon R5 M420 graphics card. I can't manage to get Ubuntu work smoothly, it crashes randomly even in the installation with live usb. As I'm totally a newbie, I can't figure out what should I do. Please help

---

### Post by yoshii on 2017-10-23
it could be a hardware problem.  did you check the sha checksum of the downloaded .ISO to make sure the file wasn't corrupt?

---

### Post by oguz-189013 on 2017-10-24
Yes I did, it was not corrupted btw. And yes I'm sure it is a hardware problem but installing proprietary drivers did not help. With nomodeset in grub conf it will not crash but nomodeset is not a solution

---

### Post by oldfred on 2017-10-24
Some possibly similar models need more boot parameters.

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by oguz-189013 on 2017-10-25
pci=nomsi gave a lot of errors just as acpi=off
nodmraid has no effect

---

### Post by gsahli on 2017-10-26
I hope you have read these, and are using the radeon (part of the distribution, not downloaded) driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://www.x.org/wiki/radeon/](https://www.x.org/wiki/radeon/)

---

