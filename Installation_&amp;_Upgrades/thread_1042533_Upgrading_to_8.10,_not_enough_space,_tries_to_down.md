---
title: "Upgrading to 8.10, not enough space, tries to download to /boot"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by zoroko on 2009-01-17
I'm trying to upgrade to 8.10 and when I use the update manager it tells me there is not enough space on /boot.  How do I change what partition it is using and make it use / ?   Why the hell is it trying to use /boot?

---

### Post by sarath_it on 2009-01-17
I am guessing you have a seperate partition and mounted it on /boot, Check with gparted how much it is worth! Generally the largest files /boot will have are kernel images. 
like

/boot/initrd.img-2.6.27-7-generic

if you have too many of these (backups) remove some and try again

---

### Post by zoroko on 2009-01-17
its a very small partition with grub and other things like the kernel. its under 200mb and about 150mb is used. 

How can I change what partition the upgrade will download to?

---

### Post by sarath_it on 2009-01-17
Well its not like what partition the upgrade *goes* into, its about what partition is mounted as what directory. Unix is different from windoze that way. So if you want to have /boot to be on a diff partition, unmount this /boot and put it to another partition. 

But 200mb should be *largely* enough for /boot. it appears you have too many backups, you can safely delete most of them, leave the latest.

---

### Post by zoroko on 2009-01-17
Thats not the point. I dont care about /boot. The point is that I can't upgrade because it wants to put the files at that point. Not install, but to store them. /boot isn't big enough regardless. The question is how do I make the upgrade store the files some where else that does have enough space, like /.

I think your missing the point. I dont care about /boot. I care about upgrading to 8.10 and the upgrade manager is trying to store the files there and that partition just isn't large enough.

---

### Post by zoroko on 2009-01-18
nobody knows anything?

---

