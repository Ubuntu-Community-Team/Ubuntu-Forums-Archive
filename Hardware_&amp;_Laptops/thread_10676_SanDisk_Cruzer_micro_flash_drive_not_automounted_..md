---
title: "SanDisk Cruzer micro flash drive not automounted ..."
date: 2005-01-10
forum: Hardware &amp; Laptops
---

### Post by minghai on 2005-01-10
Hi all, just tried out Ubuntu after playing around with Mepis and Kanotix.  How do I get my flash drive to be autodetected and automounted by Ubuntu?  This drive has no problem being automounted by Mepis and Kanotix when I plug it in so I know at least the drive is not broken.  Do I have to install autofs or supermount?  Thank you.

Ming Hai

---

### Post by hashimoto on 2005-01-10
I had a similar problem with a CF reader in Warty. sudo pmount /dev/sda got it mounted eventually, but no icon on the desktop. You may have the same problem with HAL.

I ugraded to Hoary to get my CF reader automount and show the icon. Initially I was told to upgrade HAL only, but dependency issues caused me to upgrade my whole system (I'm no guru so I thought it's best to take the path of the least resistance).

BR
Hashimoto

---

