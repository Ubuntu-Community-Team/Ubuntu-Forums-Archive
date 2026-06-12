---
title: "Restoring Ubuntu Image on a partition (from disk )"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by kartal on 2009-03-28
Hi

I was using ubuntu on my macbook pro and I only had ubuntu on it(no macos). Then  I have decided to install Macos and Windows alongside with Ubuntu. Anyways I made an image of Ubuntu disk with parted magic(partition image) then I have reinstalled macos and windows. Everything went alrigt and on top of it I have a dedicated partition for ubuntu. Now it looks like everything is fine, I also used G4L to copy original ubuntu disk to my new fully partitioned(macos, ext3, windows) macbook pro drive. I did disk to partition copy to sda3(which is ext3 on my partition table). So far so good but I cannot make grub to recognize the original grub from previous ubuntu installation(the one I copied to new partition). 

I have tried listing previously installed grubs(via grub interface) but that gives me no previous partition name at all. What is the safest way to make my ext3 ubuntu partition to bootable again.  I can see that ubuntu installation files are on that partition, it is just that I cannot make it bootable. Everything else boots fine like refit, Macos and windows.

thanks

---

### Post by zvacet on 2009-03-29
Why don´t you just [reinstall grub?]("http://ubuntuforums.org/showthread.php?t=224351")

---

