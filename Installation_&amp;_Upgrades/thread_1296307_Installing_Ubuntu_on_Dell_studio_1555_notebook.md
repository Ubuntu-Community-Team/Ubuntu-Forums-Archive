---
title: "Installing Ubuntu on Dell studio 1555 notebook"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by emorkay on 2009-10-20
Hi,
I have 500GB hard disk which has 3 primary partitions and 5 more logical partitions. All partitions are NTFS except for one of the primary partition which is FAT16. I already have Windows Vista and now I wish to install Ubuntu. How can I do that without disturbing the partitions? The partitions were created to cater for some of my specific needs and have huge data.

Thanks,

---

### Post by dabl on 2009-10-20
You need at least one partition formatted ext2/3/4 or one of the other *nix formats (reiserfs, xfs, jfs).

It's also desirable to have a swap partition, although it is possible to run without one (but no suspend-to-disk or running out of memory allowed). As an alternative to a swap partition, you can make a swap file -- Google can show you the way on that.

So, there are some decisions for you, before you get to the "how" of it.  :)

---

### Post by emorkay on 2010-06-05
Thank you for the reply. Would like to use a swap file instead of an entire partition as swap. So one partition for root and a swap file. Is that ok to install Ubuntu? Also please let me know any useful guides to make a swap file in windows and use it during installation. I would be grateful if you can tell me the installation procedure a bit detailed. Thanks.

---

### Post by davidmohammed on 2010-06-05
there are a number of guides on how to install - here is just [one]("http://www.nyutech.com/2010/04/ubuntu-lucid-lynx-installation.html").

The key one is first finding enough space to sub-divide one of your existing partitions to create a linux partition.

I would defrag your windows until you get one contiguous area (all the blue blocks in defragger are together with all white blocks to one side.  If you have files spread all over the filesystem, you will most probably lose the files that will cover the space that the new partition would exist in.

---

### Post by darkod on 2010-06-05
> **emorkay said:**
> Also please let me know any useful guides to make a swap file in windows and use it during installation.

Are you talking about windows or ubuntu here? You can't make a swap file for ubuntu in windows. Just install ubuntu without a swap partition, so only with a root partition, and then follow any of the guides how to create swap file in ubuntu.

---

### Post by emorkay on 2010-06-05
Thanks for the responses. 
1. I would like to know if swap partition or swap file is recommended. Also what is the recommended size of the swap file for the suspend hibernate options to work properly? I am cuurently using Ubuntu 10.04 Lucid 64-bit installed inside my Windows 7 Professional 64-bit using Wubi.
The size of the physical RAM in my laptop is 4 GB.
2. Can I install any Linux distribution in this way i.e., with only root partition and then making a swap file?

Thanks.

---

### Post by darkod on 2010-06-05
For hibernate to work, usually swap needs to be 1.5 x ram, so in your case with 4GB memory, swap would be 6GB.
I am not sure what is the difference between using swap partition or swap file, or if there is difference in performance.
Also I don't know about other linux distributions and whether you can create swap file in them. I know in ubuntu you can. I guess you would be able to do the same in most other linux distributions too.

If you plan to install more linux versions, it might be better to use swap partition because in that case you create just one 6GB swap partition on the hdd, and all linux versions can use it. You have only one version booted at the same time anyway, so it simply uses the swap. When you restart and boot another linux version, then that version uses the same swap partition.

---

### Post by emorkay on 2010-06-05
> **darkod said:**
> For hibernate to work, usually swap needs to be 1.5 x ram, so in your case with 4GB memory, swap would be 6GB.
I am not sure what is the difference between using swap partition or swap file, or if there is difference in performance.
Also I don't know about other linux distributions and whether you can create swap file in them. I know in ubuntu you can. I guess you would be able to do the same in most other linux distributions too.

If you plan to install more linux versions, it might be better to use swap partition because in that case you create just one 6GB swap partition on the hdd, and all linux versions can use it. You have only one version booted at the same time anyway, so it simply uses the swap. When you restart and boot another linux version, then that version uses the same swap partition.
Thanks for the reply.

---

