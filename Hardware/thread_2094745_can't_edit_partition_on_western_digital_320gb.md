---
title: "can't edit partition on western digital 320gb"
date: 2012-12-14
forum: Hardware
---

### Post by iamrandy on 2012-12-14
i have this 320gb western digital external and i am i'm trying to make it so i can use it with my ps3 and i can't get the partition to go to w95 fat32 (0x0b) please any help would be greatly appreciated [ATTACH]228670[/ATTACH]

[ATTACH]228671[/ATTACH]

---

### Post by rajhanschinmay on 2012-12-16
Simple.
First unmount the drives
sudo umount /media/drive_name

Then remount then again
mount /media/drive_name

If you mount without sudo, it would work.
If it is not allowing mounting without sudo then use
sudo mount /media/drive_name
then use
sudo chown 777 /media/drive_name

This will give u read, write and execute permissions.

Thank you.

---

