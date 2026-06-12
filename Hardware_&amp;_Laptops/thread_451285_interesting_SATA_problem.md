---
title: "interesting SATA problem"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by silvercliff on 2007-05-22
ok so i had a partition error when booting 7.04.  i thought might be a good time to dist-upgrade, and did so.  but thats not the problem.  i finally booted into linux, after getting past the error, umount'ed the partition and ran fsck on it.  great fixed all the problems on the disk.

now however i am experiencing hdd slowness.  ANY time i need to use the filesystem in any way i get a super slowdown, or even a halt.

i have a sata II 250gb seagate.

im not sure how much info i need to post, so just tell me what you need :)

---

### Post by silvercliff on 2007-05-22
found the problem and fixed it.  it seems that there was an error on my root partition, even tho fsck didnt pick it up, so i deleted the folders that were causing the problems and rebooted.  all fixed

---

