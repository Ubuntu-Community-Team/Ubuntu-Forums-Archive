---
title: "Hardy 8.04, fstab and strange behavoir"
date: 2008-05-19
forum: Hardware
---

### Post by ccafiero on 2008-05-19
Hello! I've a Ubuntu 8.04 on my Notebook Dell 6400 in the second partition (the first one is for Vista OS).

I've edit fstab for automatic mount of my Fat32 partition with shared mails for Thunderbirds (Vista anl Ubuntu) and the last line is for mounting Vista. The lines are show below

```

/dev/sda6	/media/postalinux vfat users,umask=000 0 0
/dev/sda2       /media/vista    ntfs    auto,user,umask=0222    0       0

```

Now I've two problem:

Both the mount point's name are not used for the icon of the partition displayed in the Desktop (vista mount point appears with like "device 41 GB" (thi is my translation... in italian "Supporto da 41GB"). How can change the name of the icon on desktop to be the same that the mount point "media"?

Can you help me?
Thank you alot
bye!

---

### Post by pietjanjaap on 2008-05-19
rename your label of your partition
e2label is for ext3


[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by ccafiero on 2008-05-19
> **ccafiero said:**
> Hello! I've a Ubuntu 8.04 on my Notebook Dell 6400 in the second partition (the first one is for Vista OS).

I've edit fstab for automatic mount of my Fat32 partition with shared mails for Thunderbirds (Vista anl Ubuntu) and the last line is for mounting Vista. The lines are show below

```

/dev/sda6	/media/postalinux vfat users,umask=000 0 0
/dev/sda2       /media/vista    ntfs    auto,user,umask=0222    0       0

```

Now I've two problem:

Both the mount point's name are not used for the icon of the partition displayed in the Desktop (vista mount point appears with like "device 41 GB" (thi is my translation... in italian "Supporto da 41GB"). How can change the name of the icon on desktop to be the same that the mount point "media"?

Can you help me?
Thank you alot
bye!

**************
Solved!
My partitions was with no label, renamed and solved!

---

