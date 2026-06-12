---
title: "Resizing Ubuntu partition -- more for Ubuntu, less for Win 7"
date: 2011-01-25
forum: Hardware
---

### Post by maverick280857 on 2011-01-25
Hi,

I am running Ubuntu Maverick Meerkat 10.10 on my Dell XPS 15 laptop which has one 640 GB hard disk, of which 160 GB has been allocated to Ubuntu and the rest is Windows 7 + Dell recovery partition, etc.

I want to know how I can add allocate more space to Ubuntu without having to reinstall it. I can split the Windows 7 partition from within Windows by using its Disk Management tool. This will create "unpartitioned free space" in the disk. 

All I want to do is to allocate this space to my existing Ubuntu distribution. How can this be achieved?

---

### Post by juanfpina on 2011-01-25
> **maverick280857 said:**
> Hi,

I am running Ubuntu Maverick Meerkat 10.10 on my Dell XPS 15 laptop which has one 640 GB hard disk, of which 160 GB has been allocated to Ubuntu and the rest is Windows 7 + Dell recovery partition, etc.

I want to know how I can add allocate more space to Ubuntu without having to reinstall it. I can split the Windows 7 partition from within Windows by using its Disk Management tool. This will create "unpartitioned free space" in the disk. 

All I want to do is to allocate this space to my existing Ubuntu distribution. How can this be achieved?
Use GParted or a ubuntu live cd to partition without having Ubuntu mounted.

---

### Post by maverick280857 on 2011-01-26
> **juanfpina said:**
> Use GParted or a ubuntu live cd to partition without having Ubuntu mounted.

Okay, but what if I have free unpartitioned space on my drive which I want to **add** to Ubuntu (which is already installed). How do I accomplish that?

---

### Post by ruegore on 2011-01-26
What you do is format the unpartitioned space into the same filesystem type as you have your Ubuntu partition using (ext3 or ext4?)

So for instance, I am using ext4 on the partition where I have Ubuntu installed. I then use gparted using an Ubuntu Live CD to format the unpartitioned space to ext4, then later combine the two using the Resize function.

You'll have to play around with the position of the partitions for Resize to work. Generally, the two partitions need to be beside each other. I absolutely recommend you play around with this by dividing your free unpartitioned space into two free unpartitioned spaces and see how this all works BEFORE you merge it into your current working partition. You know, it's just safer to play with a lot of nothing. :P

---

### Post by wilee-nilee on 2011-01-26
> **maverick280857 said:**
> Okay, but what if I have free unpartitioned space on my drive which I want to **add** to Ubuntu (which is already installed). How do I accomplish that?

So you want to use the W7 disk manager to resize windows, but you need to have the open space next to the Ubuntu install. So install gparted in Ubuntu and take a screen shot of it and post it.

---

### Post by maverick280857 on 2011-01-26
> **wilee-nilee said:**
> So you want to use the W7 disk manager to resize windows, but you need to have the open space next to the Ubuntu install. So install gparted in Ubuntu and take a screen shot of it and post it.

The screenshot is attached.

---

### Post by wilee-nilee on 2011-01-26
> **maverick280857 said:**
> The screenshot is attached.

So it looks as though you can shrink sda3=C with the W7 disk manager, leaving unallocated space. The problem here is that you can expand using gparted from a live cd with the swap off of course, the sda4=extended, and sda5=Ubuntu. This moving of the front of these partitions towards the front of the disc will take a long time though probably 1-2 hours, and will leave you needing to reload grub2 to boot back into Ubuntu and have grub2 as the bootloader.

Here is a link for reloading grub2 from the live cd, if needed.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Ask any more questions as needed.:)

---

### Post by maverick280857 on 2011-01-27
Is there any other way?

 I don't **have** to use Win 7's disk management tool. I can take a backup of my Win 7 files, and just use GParted or Ubuntu's Live CD to do the partitioning (Win 7 will run Chkdsk which will take care of the updated size of its partition automatically). 

But is it possible to not have to reinstall Grub, by using some other tool for repartitioning?

---

### Post by wilee-nilee on 2011-01-27
> **maverick280857 said:**
> Is there any other way?

 I don't **have** to use Win 7's disk management tool. I can take a backup of my Win 7 files, and just use GParted or Ubuntu's Live CD to do the partitioning (Win 7 will run Chkdsk which will take care of the updated size of its partition automatically). 

But is it possible to not have to reinstall Grub, by using some other tool for repartitioning?

If it was me I would shrink the windows to what you want and just reinstall Ubuntu, in the same configuration, only bigger.

---

### Post by maverick280857 on 2011-01-27
> **wilee-nilee said:**
> If it was me I would shrink the windows to what you want and just reinstall Ubuntu, in the same configuration, only bigger.

Well, I've been tempted to do that, but it would mean downloading all the updates and programs on my really slow broadband connection -- it takes about 2-4 days just to get these things. :-|

So I really hope there ought to be a better way to increase the size of the existing Ubuntu logical volume or extended partition.

---

### Post by wilee-nilee on 2011-01-27
I think shrinking W7 then expanding the extended=sda4 up against the W7 then putting another ext4 in the unallocated in the extended would work. You can make this new ext4 partition your separate home for Ubuntu. You could also just put a NTFS there as a shared for both OS's. here is a link on separate home setups.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Your swap is rather large as well, do you have 6 gigs of ram?

If not the general swap size is equal to actual ram.

---

