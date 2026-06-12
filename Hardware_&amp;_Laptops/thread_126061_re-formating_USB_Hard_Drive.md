---
title: "re-formating USB Hard Drive?"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by irv on 2006-02-05
I have a 250Gig USB Hard Drive with two partitions. One 117Gig and the other 114Gig. They are both formated with NTFS and I would like to make the 114Gig part of my Linux OS so I can read/write to it. I would also like to use it for tranfering files from windows to linux, so it needs to be formated with a format that both can read/write to it.
How do I do this? I have both partitions mounted and can read both, but can't write because of the NTFS format. Can anyone help?
Thanks

PS I have been looking for a How to? (step by step)

---

### Post by joft on 2006-02-05
Hi,

if you want do have full access from both OSes (Linux and Windows), one possibility would be to re-format the 114GB partition with FAT32:

Find out which device name is assigned to this partition, by calling:

```
df -h | grep '/media/usbdisk'
```

There will be 2 lines if at that moment the USB drive is the only device plugged in. Now you have to make sure that you identify the right one (by the second column = size of partition).

**If you are sure you found the right line**, look at the first column, that's the device name you need.

**Backup your data** on this partition before going on! **Replace <...> with the [COLOR=red]right[/COLOR] letter+number combination** found above:

```
sudo umount /dev/sd<...>
sudo mkfs.vfat -F 32 /dev/sd<...>
```

After doing that unplug and plugin the USB drive.

---

### Post by irv on 2006-02-05
Thanks joft,
This works for me, in fact, after I reformated this drive partition, I moved the files over to it from the 117Gig, and am going to reformat the 117Gig also this way I will have a ton of storage space. I use this drive for all my backups and I can see it from all my pc's on my network.
Thanks again.
Irv

---

