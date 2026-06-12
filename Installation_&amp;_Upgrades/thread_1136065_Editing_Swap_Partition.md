---
title: "Editing Swap Partition"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Skyline969 on 2009-04-24
I just downloaded GParted through Synaptic Package Manager, but it won't allow me to edit my swap partition. It just lets me view information about each partition. How can I edit my swap partition easier? If I need to download a new program, just let me know. It's not a problem for me to get one.

Thanks in advance.

---

### Post by ddrichardson on 2009-04-24
If the swap is active it needs de-activated first:```
swapoff /dev/sdaX
```You might also find that its been created as a logical drive.

---

### Post by Skyline969 on 2009-04-24
So I would just use swapoff /dev/sda5, edit the partition, then use swapon /dev/sda5? I assume I'd have to add sudo to the front as well, huh..?

---

### Post by ddrichardson on 2009-04-24
Yes

---

### Post by Skyline969 on 2009-04-24
Ok, I did that, but it's trying to tell me it's at the maximum it can be, which is 729.48 MB. What gives?

---

### Post by ddrichardson on 2009-04-24
I don't know without seeing the hard disk's geometry but if there's extra space still that it won't give you then there is an empty extended partition that needs altering before the logical partition is altered.

---

### Post by Skyline969 on 2009-04-24
Well, /dev/sda2 is my extended partition, which is 729.51 megs... should I disable sda2 and sda5, extend extended, extend linux-swap, and then enable both?

---

### Post by ddrichardson on 2009-04-25
Can you post the output of ```
sudo fdisk -l
```so I can see?

---

### Post by Big_Croc7 on 2009-04-25
Unless you have good reasons for doing this from a running system, I'd strongly recommend doing partition editing from a live CD (the GParted CD is designed for exactly this).

---

### Post by ddrichardson on 2009-04-25
> **Big_Croc7 said:**
> Unless you have good reasons for doing this from a running system, I'd strongly recommend doing partition editing from a live CD (the GParted CD is designed for exactly this).
Fair enough, if the root or home partitions are being altered.

---

