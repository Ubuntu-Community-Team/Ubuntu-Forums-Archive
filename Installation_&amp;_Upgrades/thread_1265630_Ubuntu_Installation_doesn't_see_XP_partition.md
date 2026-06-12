---
title: "Ubuntu Installation doesn't see XP partition"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by mcbenus on 2009-09-13
I am trying to install Ubuntu on an empty partition and I have XP installed in the other one.  I installed XP first and it's working fine.  The 120GB HD was partitioned when installing XP to 90GB for XP and 30GB for Ubuntu (unused yet).

I downloaded Ubuntu 9.04, burned it on CD and booted from CD to install.  After choosing the language, time, etc, it said that I have no OS installed and asked me if I want to install Ubuntu on all the HD. I quit the installation and my XP is still there and working.  

I have a DELL Vostro 1500.  

Does anyone know how to get Ubuntu to see the XP partition? Why is it not seeing the XP installed?  I read something about Gparted, do I need to use it?  BTW, what file format would work best for Ubuntu (when I will format the partition).

Thanks!

---

### Post by mikewhatever on 2009-09-13
I am not quite sure why you want Ubuntu to see Windows XP, it is, imo, completely unnecessary. Go with the manual partitioning and delete the partition allocated for Ubuntu, then quit the installation and next time, you should have an option to use the unallocated space.

---

### Post by mcbenus on 2009-09-13
The problem is that Ubuntu installation deosn't see any partition, it just sees the whole HD as one empty piece. With my XP I am able to see that I have 30GB unallocated space.  

What is the option of 'manual partitioning' you referred to? Is that in the Ubuntu installation? 

thanks!


> **mikewhatever said:**
> I am not quite sure why you want Ubuntu to see Windows XP, it is, imo, completely unnecessary. Go with the manual partitioning and delete the partition allocated for Ubuntu, then quit the installation and next time, you should have an option to use the unallocated space.

---

### Post by presence1960 on 2009-09-13
> **mcbenus said:**
> The problem is that Ubuntu installation deosn't see any partition, it just sees the whole HD as one empty piece. With my XP I am able to see that I have 30GB unallocated space.  

What is the option of 'manual partitioning' you referred to? Is that in the Ubuntu installation? 

thanks!

click manual as mikewhatever suggested you do. here is a screenshot of what he is referring to.

---

### Post by louieb on 2009-09-13
> **mcbenus said:**
> The problem is that Ubuntu installation deosn't see any partition, it just sees the whole HD as one empty piece.

One of the reasons for that is a non-standard partition table. - Most often a primary partition inside an extended partition. I've seen the windows partitioner do that.

The Ubuntu installer and Gparted are picky and if they detect a non-standard partition table they will show the drive as empty.

To check with the live CD open Applications>Accessories>Terminal 
```
sudo fdisk -l  
``` lowercase L at the end

fdisk doen't care - that command will display the partition table If you don't know what to look for please cut and paste the output in your next post.

---

