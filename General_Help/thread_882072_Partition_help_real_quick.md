---
title: "Partition help real quick"
date: 2008-08-06
forum: General Help
---

### Post by Ninjames on 2008-08-06
Just a relatively quick question. I had a thread yesterday and it was determined that I needed to reinstall Windows and then Ubuntu. The person told me to do this

"Also, since you just recently installed Ubuntu from what I gathered from your previous thread, I'd suggest starting completely fresh. Once you backup your data, boot the Windows install CD, delete ALL partitions, create a new NTFS partition of the size you want (160GB from the sounds of it) making sure there is enough free space for your Ubuntu install. On the new NTFS partitions make sure you do a FULL FORMAT, quick formats suck on NTFS and are prone to problems. Once Windows is installed, reinstall Ubuntu in the free space you left during the Windows install. This is the safest and most thorough method of reinstalling."


My question is... I made the Windows partition 160 GB, leaving me about 20 GB of unpartitioned space. I want to know if when I install Ubuntu again--will it work with that Unpartitioned space, or should I have made a second, 20 GB partition? It was listed as

D: 160 GB (my windows parittion)
C: 8 GB (my recovery partition)
and 20 GB (unpartitioned space.) So when I install Ubuntu, will it not see that? Do I have to create an actual partition for it, or will it recognize the unpartitioned space as something to work with? Thanks.

(If I need to make it a partition, should I reinstall windows all over again and make a partition and just reinstall over the 160?) Thanks, again.

---

### Post by northern lights on 2008-08-06
The partitioner in the ubuntu installation will "see" the unallocated space and is able to create peartitions in there.

When installing Ubuntu, do not select "Guided Partitioning", but rather go manual.

In the 20GB unallocated space create either

18GB  /     ext3
 2GB  SWAP  swapspace

or

10GB  /     ext3
 8GB  /home ext3
 2GB  SWAP  swapspace

---

### Post by nbayiha on 2008-08-06
If you want to install ubuntu , you can do it with your 20giga disk . I just dont understand why u keep so low space for ubuntu ? Just 20giga , anyway i guess it's not your primary OS .
So dont forget that during your installation of Ubuntu you will have to do three partition of the 20gi disk.
/swap partition 
/home partition 
/ (system) partition .
If you dont know what i am talking about ,let the cd  automatically partition your 20gi disk.

---

