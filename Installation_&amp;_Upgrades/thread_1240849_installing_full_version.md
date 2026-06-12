---
title: "installing full version"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Jimstehrman on 2009-08-15
hello,

I'm trying to put ubuntu on a 140 Gb partition on my HDD. While installing I come to a screen asking me to select the pat of my partition I want to use. I select it, and then it says I need to edit my partition, and prompt comes up asking how much I want to use, what file system, and what mount point. This seems like it is heading into dangerous territory, I hear that when Linux formats a partition, Vista gets pretty worked up about it. Is it safe to let linux edit the partition? and if so, which values would be best to input?

thanks for your time.

---

### Post by lisati on 2009-08-15
I've heard of Vista getting confused when Ubuntu's partitioner is used to change Vista's partition. I had it happen myself once but didn't make the connection at the time due to trying to do several things at once.

Some of the wisdom I've read in the forums is to use Vista's partition manager, if possible, to resize Vista's partition(s) first to free up some space for Ubuntu. You can then do something like tell Ubuntu's installer to use the largest continuous free space.

As usual, it's a good to make backups (including recovery partitions & disks) before making any major changes.

---

### Post by presence1960 on 2009-08-15
> **Jimstehrman said:**
> hello,

I'm trying to put ubuntu on a 140 Gb partition on my HDD. While installing I come to a screen asking me to select the pat of my partition I want to use. I select it, and then it says I need to edit my partition, and prompt comes up asking how much I want to use, what file system, and what mount point. This seems like it is heading into dangerous territory, I hear that when Linux formats a partition, Vista gets pretty worked up about it. Is it safe to let linux edit the partition? and if so, which values would be best to input?

thanks for your time.

if you don't edit that partition thru the installer as asked you will not be able to install. Make sure for mount point you select /. For file system either ext 3 or ext 4. relax it is not dangerous, you are only editing the partition you are installing Ubuntu to. As long as you used Vista's disk management utility to shrink Vista's partition to create space for Ubuntu you are ok. If you used gparted Live CD or Ubuntu Live CD to shrink Vista's partition you may have a problem with Vista.

---

### Post by Jimstehrman on 2009-08-15
thanks for the tips, my partition came pre-configured with my comp, so I don;t need to select the format option?

---

### Post by presence1960 on 2009-08-15
> **Jimstehrman said:**
> thanks for the tips, my partition came pre-configured with my comp, so I don;t need to select the format option?
 You don't have to, but that has nothing to do with the fact of whether that partition came with your machine or you created it. What format will do is erase all data off that partition prior to installing Ubuntu onto it. Personally I always tick the format box when installing that way I am certain I have a clean partition prior to the installer putting Ubuntu on there. But it isn't absolutely necessary.

---

