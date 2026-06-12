---
title: "How to unlock sdb with same encryption password as OS disk?"
date: 2020-10-16
forum: Hardware
---

### Post by chr1sM on 2020-10-16
Hi,

I have an encrypted Ubuntu 18.04 server with disks as below. I am going to reformat and encrypt sdb.

What is the smartest way to encrypt sdb so it is unlocked with the same password as sda on boot?  

sda                     8:0    0 465.8G  0 disk
&#9500;&#9472;sda1                  8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                  8:2    0   732M  0 part  /boot
&#9492;&#9472;sda3                  8:3    0 464.6G  0 part
  &#9492;&#9472;sda3_crypt        253:0    0 464.6G  0 crypt
    &#9500;&#9472;srv--vg-root   253:1    0 463.6G  0 lvm   /
    &#9492;&#9472;srv--vg-swap_1 253:2    0   980M  0 lvm   [SWAP]
sdb                     8:16   0 465.8G  0 disk
&#9500;&#9472;sdb1                  8:17   0   100M  0 part
&#9500;&#9472;sdb2                  8:18   0 455.9G  0 part
&#9492;&#9472;sdb3                  8:19   0   9.8G  0 part
sr0                    11:0    1  1024M  0 rom

Thanks,

Chris

---

