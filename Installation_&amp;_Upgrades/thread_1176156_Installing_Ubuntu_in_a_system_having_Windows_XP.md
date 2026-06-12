---
title: "Installing Ubuntu in a system having Windows XP"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by raam_baala on 2009-06-02
Dear All,
I'm a new user of Ubuntu. 
1.) I've a PC with windows-XP already installed. My harddisk is 160GB with the partitions C: (Windows home)[40GB], D:,[40GB],E:[40GB], F:[40GB]. I've installed UBUNTU 8.04 on the F: partion assigning the Ext 3 file system. 
During installation, UBUNTU gave a warning that there is no space for "Swap", but the partition has 40GB space. Why is it so?
 
2.) After proceeding with installation, I'm not able to view the F: partition in Windows. Can anyone explain me why?
 
3.)When I try to open C:, D: or E: partitions form Ubuntu, they are read-only. How to solve this problem.
 
As I'm very new to Ubuntu, kindly advice me accordingly.
Thank You in advance.

---

### Post by AlexsAntidote on 2009-06-02
You don't want to use a 40GB partition for your Swap, that would be overkill. Think of the Swap as virtual memory (Windows) or a Paging File. Linux uses a Linux-Swap partition to supplement your RAM. I'm not very technical on this, but I do know it is needed, so you would do well to resize one of your partitions (probably just shrink then end of your Ubuntu partition) and create a new partition (a Linux-Swap). It is recommended that your swap partition is equal to or greater in size to your physical RAM. So if you have 1GB of RAM your swap should be at least 1GB. See here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

**Edit: read here for more info on swap - [http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space) :End Edit**

You are not able to view the Linux partition in Windows because Windows does not have native support for reading/writing Ext file systems. There is a program out there you can download that allows you to read/write Ext2/Ext3 file systems, but you'll need to google for it.

**Edit: something like this maybe? [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) :End Edit**

I'm going to guess your "C:, D:, and E:" partitions are NTFS. You will need to enable NTFS support to write to them.

**Edit: read this for more info - [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G) :End Edit**

---

### Post by sahabcse on 2009-06-02
Boot from ubuntu Cd and partition part find out your F: drive and remove the partition, then it show like free space there you create swap partition (size double of your RAM or more) remaining space give for / partition.

---

### Post by raam_baala on 2009-06-02
Thanks Alex. i'll try this and get back to you.

---

### Post by AlexsAntidote on 2009-06-02
> **sahabcse said:**
> Boot from ubuntu Cd and partition part find out your F: drive and remove the partition, then it show like free space there you create swap partition (size double of your RAM or more) remaining space give for / partition.

I believe the OP mentioned Ubuntu was installed on the "F" partition. If the "F: drive" is removed then the OP will need to reinstall Ubuntu.

---

### Post by AlexsAntidote on 2009-06-02
You're welcome raam_baala, I hope it works out for you without any trouble.

---

