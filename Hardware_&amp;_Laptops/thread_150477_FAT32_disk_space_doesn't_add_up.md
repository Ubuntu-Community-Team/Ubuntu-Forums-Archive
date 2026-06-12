---
title: "FAT32 disk space doesn't add up??"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by robinl on 2006-03-26
Hi I have a 53GB FAT32 partition which originally have 15GB free space left. Then I installed windows on a sperate NTFS partition and it have 14GB left after installing some games. THEN I go back to ubuntu for a night and go to windows the next day, and BAM I only have 700kb left. I did absoulutely nothing on it on either ubuntu or windows so where had the free space gone? In ubuntu if I select everything and check properties it give me 38.9GB are used for them, which means that I should have about 14GB of free space left, and yet it shows 350MB left in system monitor and other places (after deleting some things). This is not right. Something is eating my spaces and yet I cannot see them. Any help? ](*,)

---

### Post by localzuk on 2006-03-26
Hi, on a terminal type ```
df -h
``` so we can see what is mounted and what is what.

---

### Post by robinl on 2006-03-26
Hi here's the output of df -h
```
/dev/hda1             9.2G  8.0G  809M  91% /
tmpfs                 761M     0  761M   0% /dev/shm
/dev/hda6             7.5G  5.9G  1.6G  79% /windows/hda3
/dev/hda3              54G   54G  342M 100% /windows/hda4
/var/www              9.2G  8.0G  809M  91% /home/FTP-shared/download
/var/www/michelz      9.2G  8.0G  809M  91% /home/FTP-shared/upload
/dev/hdc              629M  629M     0 100% /media/cdrom0

```

The FAT32 partition is /dev/hda3 which is mounted on /windows/hda4 because appearantly the installation of windows jumbled up the numbers.

---

