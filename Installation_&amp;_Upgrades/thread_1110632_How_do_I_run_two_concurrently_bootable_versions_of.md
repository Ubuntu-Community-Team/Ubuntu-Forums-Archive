---
title: "How do I run two concurrently bootable versions of ubuntu?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by lxowle on 2009-03-30
I've read on the forums from time to time about people who can boot to different versions of ubuntu (i.e., 8.10 and 9.04 beta) and now I want to be able to do this so I can try new versions of ubuntu, but still use the older version if I want to.

At the moment, my partitions look like this:
```
sda1 - windows
sda2 - 10gig, / (ext4) ubuntu 9.04
sad3 - 100gig /home (ext3)
sda4 - swap

```
I will use something to shrink the windows partition by 10 or so gig and I guess I will end up with:
```
sda1 - windows
sda2 - 10gig, / (ext3) ubuntu 8.10
sda3 - 10gig, / (ext4) ubuntu 9.04
sad4 - 100gig /home (ext3)
sda5 - swap
```
 
But, what do I call the different mount points - they both can't be '/' can they? For both versions of ubuntu, I want to be able to use my /home directory on the other partition as default home - will I be able to that?

---

### Post by divague on 2009-03-30
> what do I call the different mount points - they both can't be '/' can they? 

Both can be / beacause they will be on different partitions.

> For both versions of ubuntu, I want to be able to use my /home directory on the other partition as default home - will I be able to that?

Yes, i think you can share you /home partition with both versions.

---

### Post by lxowle on 2009-03-30
> **divague said:**
> Both can be / beacause they will be on different partitions.


Great thanks - I had no idea it would be so simple! G-parted can resize partitions without formating them can't it?

---

### Post by Cybie257 on 2009-03-30
> **lxowle said:**
> I've read on the forums from time to time about people who can boot to different versions of ubuntu (i.e., 8.10 and 9.04 beta) and now I want to be able to do this so I can try new versions of ubuntu, but still use the older version if I want to.

But, what do I call the different mount points - they both can't be '/' can they? For both versions of ubuntu, I want to be able to use my /home directory on the other partition as default home - will I be able to that?

One thing I do to keep things organized, is use a second hard drive with another version. Installing the second install while the other is disconnected so the Grub won't affect it. Then I use the BIOS options to decide which drive I want it to boot from (when both are connected). This works for me, but if you only have one hard drive, then I see another post that has already put you in the right direction. I can also access any information from either install, but be aware that if you test with jaunty and use Ext4, you'll have to get a bit tricky with getting Ext4 compatibility with older versions. That is if I just haven't come across an easy way to add Ext4 support in the older versions, so i had tried installing a newer kernel (from Jaunty repos) in to Intrepid. It works to access, but broke a lot of my working programs, but I was able to simply remove the menu.lst option for that kernel and get back to my working kernel version. 

-Cybie

---

### Post by divague on 2009-03-30
> G-parted can resize partitions without formating them can't it?

Yes, i suggest you to use the gparted livecd

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by lxowle on 2009-03-30
Thanks for the help everyone. I'll have a got at it next week when some of my deadlines are in and let you know how it went.

Good advice about getting a second harddrive as well. They are cheap now and it would make backing up a lot easier.

---

