---
title: "LaCie USB Drive, 10MB?"
date: 2008-10-20
forum: Hardware
---

### Post by ilovebrownies on 2008-10-20
Hello fellow Ubuntuers.

I've been using Ubuntu for a couple of months now, and aside from a couple of minor issues, I'm loving it.

Now for my latest problem. I recently purchased a LaCie 1TB USB Drive, and when I plugged it in, it mounted, but it only shows up with a total size of 10MB. I used gparted to try and make sense of it, but it shows up with two partitions, one with no size, which Ubuntu can't seem to identify the file system of, and one 10MB partition which it says is in hfs file system. It does say that it has 900GB or so of unallocated space, so I tried deleting all the existing partitions and creating one full sized ntfs partition, but that didn't work.

Can any of you gurus shed some light on my situation?

---

### Post by ilovebrownies on 2008-10-20
bumpage

---

### Post by Curvature_Tensor on 2009-06-10
Here is how to fix this

sudo apt-get install gparted
sudo gparted

goto /dev/sdb
Click "Device"
Click "Create Partition Table"
Select ext3 file format

now when your external hard drive will auto mount as /media/disk/ with the proper memory (I list about 20 GB out of 320 GB when I did this, I assume this is due to formating to a different data type)

---

