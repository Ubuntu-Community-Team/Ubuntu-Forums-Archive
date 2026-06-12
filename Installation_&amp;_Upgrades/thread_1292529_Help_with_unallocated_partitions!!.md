---
title: "Help with unallocated partitions!!"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by gordonr785 on 2009-10-15
Trying to install Ubuntu on a Inspiron 1720. I want to dual boot with Vista, Vista is already installed. I used Ubuntu to shrink my existing C: drive to give me 10 gigs unallocated space. When I attempted to install Ubuntu, I got to the preparing disk part. I selected for it to install along side Vista. It then went into resizing the partition, after about 10 minutes it stopped and said it was unable to use the disk space. I stopped it at that point. On booting back up to Vista and going to the disk management, I see I now have two unallocated partitions. Can I delete the two unallocated partitions without losing Vista? I would then try and install Ubuntu
 
Thanks, Bob

---

### Post by oboedad55 on 2009-10-16
> **gordonr785 said:**
> Trying to install Ubuntu on a Inspiron 1720. I want to dual boot with Vista, Vista is already installed. I used Ubuntu to shrink my existing C: drive to give me 10 gigs unallocated space. When I attempted to install Ubuntu, I got to the preparing disk part. I selected for it to install along side Vista. It then went into resizing the partition, after about 10 minutes it stopped and said it was unable to use the disk space. I stopped it at that point. On booting back up to Vista and going to the disk management, I see I now have two unallocated partitions. Can I delete the two unallocated partitions without losing Vista? I would then try and install Ubuntu
 
Thanks, Bob

First of all, anytime you're messing with partitions be sure to back up anything you don't want to lose. Usually things are fine, but just in case. You should be able to delete the two partitions and create a new one. Ideally, you should create a swap partition about the same size as your ram and then another partition for the Ubuntu install. Then when you go to install you select to manually partition and select the ones you just made. Sounds complicated. go slow and be sure of what you're doing.

---

### Post by gordonr785 on 2009-10-16
Thanks for the response.  I have it going now.

---

### Post by jward3010 on 2009-10-16
Yay!

The good news about Ubuntu and installing it after a Windows system is already in place is that it knows about it and gives entries for it so experiment away, you'll learn very quickly.

---

