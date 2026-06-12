---
title: "serial hard drive ntfs mounting"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by rezfiles on 2005-07-05
I have been using ubuntu live for a long time. But recently my windows xp pro installation has crashe, and i am tired of it. I just installed ubuntu on my secondary serial ata hard drive, the primary is there so i can back up the files. Now to back up the files how do i mount that hard drive? it is serial ata. Thanks

---

### Post by intangible on 2005-07-05
I believe this will get you going:

sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows

If that doesn't seem to work, type this into a terminal window and give me the output:
**sudo fdisk -l**

---

### Post by rezfiles on 2005-07-05
THANK YOU!!!!!!!!!!!!!!!!
lol, hanx for the help

---

