---
title: "Partition Q's from a Fedora Refugee"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Snarfblat on 2009-02-06
I'm switching to Ubuntu (KUbuntu to be specific) 8.10 from Fedora, because I can't get Eclipse 3.3 to run on Fedora 10 and nobody seems to know why.

One thing I noticed about Ubuntu is that it doesn't have an "auto configure" option during installation for partitioning, like Fedora does.  So, I have some questions.

I have a 320 gig drive in my Laptop (Inspiron 1520), and most of it is taken up by Vista... a 100g C: and 190g D:, leaving 30g for Linux.

What I've gotten from searching for "partitioning" is that I need a /swap drive the size of my RAM, and then any others should be created inside a logical partition.  What I don't understand is what Ubuntu calls its logical volumes.  Fedora calls them LVM, but I don't see anything like that listed in the partition manager in the installer.  I see ext2, ext3, and some variations on Journaling Filesystems and that's it.

Does Ubuntu need any kind of /boot partition like Fedora?  I'm not sure what my boot manager options are in that respect.  I've had trouble with past Fedoras (such as 8, the last one that I had working) not properly installing the boot manager, and having to go in manually afterward and tweak it.

Thanks for your help!

Rob

---

### Post by Pumalite on 2009-02-06
You don't need a /boot partition. When you install; go 'Manual' and use the old Fedora partitions. You need to give one of them mount point '/'. You can ignore /swap
(format ext3)

---

### Post by ibutho on 2009-02-06
> I'm switching to Ubuntu (KUbuntu to be specific) 8.10 from Fedora, because I can't get Eclipse 3.3 to run on Fedora 10 and nobody seems to know why.

Did you post a support question for this somewhere? I use Sun Java on Fedora 10 and apps like Netbeans and Eclipse just work.

> 
What I've gotten from searching for "partitioning" is that I need a /swap drive the size of my RAM, and then any others should be created inside a logical partition. 
You don't necessarily need to make the swap space the same as the ram. I have 512MB swap and 1024MB ram and my swap is barely touched. LVM = Logical Volume Manager which is the same thing that Ubuntu calls Logical Volumes. As for a /boot partition, you can do without one (on any distro). For the bootloader, during installation, click on the advanced tab and you will have an option to tweak the bootloader to your liking.

---

