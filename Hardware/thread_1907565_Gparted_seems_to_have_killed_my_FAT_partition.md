---
title: "Gparted seems to have killed my FAT partition"
date: 2012-01-11
forum: Hardware
---

### Post by mistafeesh on 2012-01-11
Hi, I have a 1TB external HDD (SATA drive in USB2 box) which has a ext4 partition and a FAT32 partition. I was trying to move everything from the ext4 to the fat partition. Using gparted, I shrunk the ext4 one successfully but something went wrong when I was growing the fat one and now it won't mount. 
I ran 'dosfsck /dev/sdb1' and the message was 'Logical sector size is zero'...

any idea if there's anything I can do?

---

