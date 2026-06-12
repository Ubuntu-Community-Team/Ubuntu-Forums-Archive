---
title: "Question about manually setting partitions"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Wackjob on 2009-05-18
I want to try out Ext4 with Ubuntu 9.04, so I guess I need to manually setup the partitions in the installation menu. 

Anyhow, do these partitions look alright or am I missing something? I was planning on using 3 partitions on the same hard drive, which are...

/boot (500 mb)
swap (3000 mb)
/ (rest of the free space)

I've never manually setup partitions in Linux, so I am uncertain if I need more (or less?) partitions. Do my settings look alright or do I need to alter a partition?

---

### Post by cvielma on 2009-05-18
Hi there!

Do you know what mean each partition?
You may get an idea [here.]("http://tldp.org/HOWTO/Partition/requirements.html#number")
Maybe it's a little outdated but it have some information. 

Well, i'd recommend you to use just one / partition instead of one /boot and one /. 

Another thing is that the swap partition is recommended to be the double of your ram memory if you have less than 512 MB. But more than that should be of the same size. When i install ubuntu with 1GB or more i only set swap at the half size (i.e.: if i have 2GB RAM i use 1Gb of swap). 

Maybe you must leave / at ext3, and partition /home or another personal partition with ext4, for the sake of the system.

I haven't test ext4 yet, i did with reiserFS and i leaved / as ext3 and /home, and other 3 personal-use partitions with reiserFS to test without having any problem with ubuntu.

I hope i helped you!

Greetings!

---

### Post by logos34 on 2009-05-18
> **Wackjob said:**
> 
/boot (500 mb)


maybe you're thinking you need an *ext2/3* /boot for grub and ext4?  But that was only an issue with upgrading to 9.04 beta. i.e.:

> 
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
Ext4 support in GRUB was provided by Colin King. If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 9.04 Beta to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot.

---

