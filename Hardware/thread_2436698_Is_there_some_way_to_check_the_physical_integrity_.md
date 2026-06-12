---
title: "Is there some way to check the physical integrity of hard drives under Ubuntu?"
date: 2020-02-11
forum: Hardware
---

### Post by raphaell2 on 2020-02-11
Is there some way to check the physical integrity of hard drives under Ubuntu?

---

### Post by slickymaster on 2020-02-11
Check this thread [https://askubuntu.com/questions/59064/how-to-run-a-checkdisk](https://askubuntu.com/questions/59064/how-to-run-a-checkdisk)

---

### Post by raphaell2 on 2020-02-11
Thank you. Badblocks seems to work as advertised. I'm fairly sceptical about the Disks utility, though - it might get ext4 partitions right, but when I tell it to check my ntfs partition, it tells me instantly, within a split second, that everything is fine, and somehow I doubt that it does a thorough check within that split second. (And that happens no matter whether I use sudo or not.)

---

