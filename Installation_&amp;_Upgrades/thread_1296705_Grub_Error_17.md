---
title: "Grub Error 17"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by justgrant2009 on 2009-10-21
Ok gang, so I had windows vista on my toshiba laptop, got a little frustrated with it after a couple crashes one night.  I had already set it up to dual boot vista and kubuntu 9.04, and had intended to switch kubuntu to ubunut (don't ask why, i'm weird) anyways, in installing ubuntu, i accidently added it instead of just overwriting the kubuntu partition, and naturally, it installed ubuntu in nothing more than a 2.5 Gb partition... worthless... So i popped in my gparted disk to change things up a bit.  I deleted the kubuntu partition ( not a swap or anything, just the spot that had kubuntu) then I coppied the ubuntu partition over to where the kubuntu was (still haven't deleted the original though) and now when i rebooted it.  The grub menu stops and tells me error 17.  HELP i'm in panic because i have several things on my vista partition i need for school work.  I looked around and have found a few things about super grub, so i downloaded it and made a disk, but before i do anything with it, i would like to know what it is i need to do with it, because obviously I've gotten myself in a heap of hurt.  Please, help, asap.

Grant

---

### Post by tommcd on 2009-10-21
> **justgrant2009 said:**
> So i popped in my gparted disk to change things up a bit.  I deleted the kubuntu partition ( not a swap or anything, just the spot that had kubuntu) then I coppied the ubuntu partition over to where the kubuntu was ...

How did you copy the Ubuntu partition to where Kubuntu was?

The proper way to do this would have been to delete the Kubuntu partition with the GParted live CD. This will create unallocated space where Kubuntu was. Then use the GParted live CD to resize the Ubuntu partition to take up the unallocated space that was created when you deleted Kubuntu. This will only work if the Ubuntu and Kubuntu partitions are contiguous on the hard drive though. If they are, then do that.
If they are not contiguous or you run into trouble doing that, then since you just did a fresh install of Ubuntu, and since you need to get to Vista urgently for school, I would recommend using the GParted live CD to delete both the Ubuntu and Kubuntu partitions. Then do a clean install of Ubuntu onto the unallocated space that was created from deleting the Ubuntu and Kubuntu partitions.
Of course, first backup any important data you may have in your home directory first.

---

### Post by raprap30 on 2009-10-21
Reinstall Grub with the Ubuntu live CD. BTW what is ubunut?

---

### Post by justgrant2009 on 2009-10-21
Tommcd, if i am going to just delete the kubuntu and ubuntu partitions, they also have "swap"s between them (little red partitions on the gparted view) should i delete them as well?

---

### Post by tommcd on 2009-10-22
> **justgrant2009 said:**
> Tommcd, if i am going to just delete the kubuntu and ubuntu partitions, they also have "swap"s between them (little red partitions on the gparted view) should i delete them as well?
Yes, you may as well and just start over. The Ubuntu installer will create a swap partition for you when you reinstall Ubuntu.
If you have enough hard drive space I would recommend also creating a separate home partition for your data files. If you want to do this, then choose manual partitioning and create: a 10-12GB root partition, a 1GB swap partition, and the rest for home. Here is a good tutorial on installing Ubuntu:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
And for the manual partitioning with a separate home partition:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
If you don't have enough space for this then just set up a root and a swap partition. That will work fine also.

---

### Post by carmoneyfast on 2009-10-22
Grub error 17 and Grub error 15, the most common grub error messages. Grub error 17 is kind of scary because you don’t even see your grub menu in this case and grub error 15 is very frustrating because it shows the grub menu but comes back to same error over and over again. I was also terrified of these error because once you get these error you can’t use your system, you can’t access the net and that’s is just not cool.is it ?

The reason for grub error 17 is a messed up partition table disk order. How partition table disk order gets messed up I have no idea but it does sometimes and then you get error 17. So what does it mean by a messed up partition table disk order. It means say your drive A was /dev/hda2 earlier now it is /dev/hda3 or something else bottom line for you to know is that you need to fix this to get rid of error 17. A good way to find this out is using a live CD

---

