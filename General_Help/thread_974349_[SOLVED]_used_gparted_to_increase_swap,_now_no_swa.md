---
title: "[SOLVED] used gparted to increase swap, now no swap"
date: 2008-11-07
forum: General Help
---

### Post by csmaster2005 on 2008-11-07
my swap partition was only ~500 megs big, so I used gparted to increase it (since it was too small of a partition to go into hibernate, so I needed to increase it)
gparted worked successfully, and it IS bigger, but now ubuntu doesn't even detect a swap. When I do top, it returns swap size of 0

is there something I'm missing?
thanks

---

### Post by drs305 on 2008-11-07
If swap is designated by UUID in fstab, check that swap line in fstab matches the swap UUID. (If by device, check device is still the same - e.g. sda7, sdb2, etc)
```

sudo blkid 
cat /etc/fstab | grep swap

```
If they don't match, make the change in fstab.

Additionally, the UUID in /etc/initramfs-tools/conf.d/resume should be the same as the swap UUID. If it is not, make the change to the 'resume' file.

```

cat /etc/initramfs-tools/conf.d/resume
*if doesn't match current UUID*
gksu gedit /etc/initramfs-tools/conf.d/resume
*make the changes and save*
sudo update-initramfs -uk all

```
Reboot

---

### Post by conscious on 2008-11-07
When I resized my swap, I used the following procedure:

First, set up a swap area:
```
sudo mkswap /dev/sd*xx*
```
(where /dev/sd*xx* is swap partition).

Then, edit /etc/fstab to update the UUID of the swap partition:
```
sudo blkid
gksudo gedit /etc/fstab
```
(replace the UUID in the line that contains "swap" with what blkid returned).

Finally, turn it on:
```
sudo swapon -a
```

---

### Post by csmaster2005 on 2008-11-07
thanks drs345. What you said worked like a charm :)

Any idea why it needs to be manually updated, and doesn't get automatically changed?

---

### Post by drs305 on 2008-11-07
> **csmaster2005 said:**
> thanks drs345. What you said worked like a charm :)

Any idea why it needs to be manually updated, and doesn't get automatically changed?

Glad you got this issue resolved.

Except for designating partitions during an install, I don't think fstab is ever updated automatically. I can't tell you why it was decided to go that route but maybe somebody else can. 

Once you have that question (or others) answered please don't forget to mark this thread 'Solved' via the 'Thread Tools' link at the top right of the first post.

Welcome to the ubuntu forums.

---

