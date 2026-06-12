---
title: "Hard disk inaccessible"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by ignorance on 2006-03-20
Just formatted a hard disk and was planning to use it so i did everything with cfdisk, now just i wanted to use the disk the disk manager states that the disk is inaccessible. So what did i forget or did wrong? I'm going to use it as a secondary disk so no os on that one just files and stuff like that.

---

### Post by taurus on 2006-03-20
Did you format it under Ubuntu and what filesystem did you format it to?  See if you can mount it manually as
```

sudo mkdir /mnt/second
sudo mount -t ext3 /dev/hdb1 /mnt/second
(assuming that you formatted it as ext3...)
df -h

```

---

### Post by gnu2tux on 2006-03-20
Remember you need to make the filesystem (eg format it) after partitioning with (c)fdisk:

mkfs.ext3 /dev/hdX

---

### Post by ignorance on 2006-03-20
well that doesn't work but i got this from it

```

sudo mount -t ext2 /dev/hdb1 /mnt/second
mount: /dev/hdb1 already mounted or /mnt/second busy
mount: according to mtab, /dev/hdb1 is mounted on /

```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              74G   37G   34G  53% /
tmpfs                 380M     0  380M   0% /dev/shm
tmpfs                 380M   13M  367M   4% /lib/modules/2.6.12-10-386/volatile

```

---

### Post by taurus on 2006-03-20
Well, you mount your second harddrive as /!!!  What does your /etc/fstab look like then?
```

more /etc/fstab

```

---

### Post by ignorance on 2006-03-20
well i thank you for your help all but i just got tired of faling so i installed debian on it. But thnx for the help all.

---

