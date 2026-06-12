---
title: "New hard drive"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by fishamit on 2007-05-10
I just installed a new 120 gig hard drive, in addition to my 80 gig (containing 2 partitions, ubuntu+winxp)

so now i have:
80 gig, windows xp and ubuntu, NTFS
120 gig, empty, NTFS


my problem is that i don't have write permission to the new drive from linux (only to access files).

The drive is already empty, so i don't mind formatting it or anything. my question is, what should i do so that i'lll have full write permission to the new 120 gig drive?(from root)

---

### Post by trak87 on 2007-05-10
Format the new drive as fat32 rather than NTFS.

---

### Post by fishamit on 2007-05-10
one more question,
is there a way to make this drive "permenantly" mounted into ubuntu? so that i don't have to mount it every time?

---

### Post by taurus on 2007-05-10
Here you go.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by fishamit on 2007-05-10
Thank you both :)

---

### Post by trak87 on 2007-05-10
What is status of the ntfs-3g driver as far as writing to ntfs from Linux and avoiding drive corruption? Is it really safe to use?

---

