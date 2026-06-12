---
title: "New install of Ubuntu 8.10 and ext4 filesystems"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by japju on 2009-02-04
I want to install Ubuntu Server 8.10 to a new system that has no operating system and will not be a dual boot machine. So far, so good. But I want to use ext4 files systems from the start.

The plan for the installation is to burn the ISO image, etc....

As far as I understand, Ubuntu 8.10 Server comes with kernel 2.6.27-server, but according to [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto), the support for ext4 was added to kernel version 2.6.28.

Anyone have any suggestions how to proceed? I want the stability of the 8.10 release, but newever kernel version. And I want all the partitions with the possible exception of /boot to be ext4.

thanks,

Jari

---

### Post by Slim Odds on 2009-02-04
So... you are basically asking the impossible.

8.10 does not support ext4. So either use 9.04 or use ext3.

Otherwise, you can build a custom kernel.

Those are your choices.....

---

### Post by japju on 2009-02-04
I should have been clearer what I am after:

I don't mind building a new kernel. I also do have access to another Ubuntu box which I can update to 8.10 before starting the new installation.

But is there some way of using 8.10 packaging of application and so on, but 

1) use a custom kernel instead of selected set offered by the 8.10 install

2) and allow ext4 as a fs choice during install

I'm plenty familiar with Linux but not all that used to Ubuntu packaging or installation scripts.

thanks,

Jari

---

