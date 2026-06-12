---
title: "Dual ubuntu - Partition huge problem- urgent"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by draxz on 2009-02-04
Hello again,

here is the problem, it seems I have two ubuntu OS and XP installed(check the pic)


I booted the livecd and click installed to check the partition, it shows two Ubuntu OS. This whole problem came about when I used partition editor to give more space to XP. 

I removed about 2 GB from Ubuntu , but it was created as a unallocated drive so I deleted using disk manager in XP and then put it back in Ubuntu.

Please any one help??

---

### Post by Pumalite on 2009-02-04
According to your pic of sda; you have 6 GB+ for XP (ntfs), followed by an extended partition within which you have 1 Ubuntu in a logical partition of 49+ GB

---

### Post by caljohnsmith on 2009-02-04
Actually you have only one Ubuntu partition sda5. sda2 is what is called an "extended partition", and it is just a container for your logical partitions. Your only logical partition is Ubuntu on sda5. Your partitioning looks fine, although I'm a little surprised you don't have a swap partition.

---

### Post by draxz on 2009-02-04
I had allocated 6GB for Xp and the remaining for UB. 

So it it mean I have only one UB. OS and Xp which is 6Gb
Then why does in the boot menu shows two ubuntu and two Ubuntu recovery option and XP

How can I add more space to Xp 

I tried using Gparted to reduce 5 GB from UB. but the 5GB now shows as unallocated space 

How do I add it to XP

---

### Post by draxz on 2009-02-04
> **caljohnsmith said:**
> Actually you have only one Ubuntu partition sda5. sda2 is what is called an "extended partition", and it is just a container for your logical partitions. Your only logical partition is Ubuntu on sda5. Your partitioning looks fine, although I'm a little surprised you don't have a swap partition.

I am totally new to this, What is a swap partition
I just inserted the CD, booted from it  and followed the instructions to install Ubuntu.Am I missing some thing

---

### Post by Pumalite on 2009-02-04
You can use Gparted from the live CD . Better is Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Pumalite on 2009-02-04
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by draxz on 2009-02-04
Hello,

I ran the live cd and reduced the linux space by 4 gb

So now I have an unallocated space. How do i add this to XP

I selected Xp and clicked resize/move but I am only able to reduce its space and not increase it

Cant help?

---

### Post by louieb on 2009-02-04
You  need the unallocated space next to sda1. 1st you have to shrink sda5 from the left. 2nd you have to shrink sda2 from the left. Then you can add the space to sda1.

---

### Post by draxz on 2009-02-04
I have added back the unallocated space back to the linux OS 

now I am shrinking sda5 from the left and shrinking sda2 from the left.

then I add it to SDa1?

---

### Post by louieb on 2009-02-04
> **draxz said:**
> then I add it to SDa1?

or I could have worded it the grow sda1 to the right.  

Since you have moved the start of the Linux partition you may have to setup grub again. Its not hard takes a couple of minutes. 
Boot the live CD.
open applications>accessories>terminal
then enter```
 
sudo grub
``` 
this gets you the **grub>** prompt now enter
```
root (hd0,4)
```
and
```
setup (hd0)
```
and your done to get out enter
```
quit
```

or you can get a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") and let it do it for you. Its a handy disk to keep around.

---

### Post by draxz on 2009-02-04
So this is wht I have done.

I moved now I am shrinking sda5 from the left and shrinking sda2 from the left . its taking 1and 30 min for the first one and 2 hours for the second one. So after its done I will have an unallocated space, then like u said I can add space to sda1?

---

### Post by draxz on 2009-02-05
so after 5 hours I have finished it, giving more space for Xp

just wondering why its still showing unallocated space

---

### Post by halovivek on 2009-02-05
you cannot use the unallocated space of 7-8 MB because it is used for cylinder and memory allocation data in the hard disk. So dont worry. Every hard disk does that.

---

### Post by Liakath on 2009-02-05
Dear draxz,

> **draxz said:**
> Hello,

I ran the live cd and reduced the linux space by 4 gb

So now I have an unallocated space. How do i add this to XP

I selected Xp and clicked resize/move but I am only able to reduce its space and not increase it

Cant help?

To expand your NTFS the unallocated space must be adjacent to it; whereas in your case the Ubuntu partition is in between the NTFS partition and the unallocated space.

Now to get the result you want you have to expand the Ubuntu partition to include the the unallocated space and then shrink it from left (ie from the start of the partition) and then use that space to expand the NTFS partition. Of course these operation are to be done from either a Live CD environment or using GParted CD.

Hope this answers your requirement.

Liakath

---

### Post by carml on 2009-02-05
The best way to manage disks IMHO is to boot with Gparted Live,so you have the total control over your partitions,because they aren't in use.Doing so you'll be able moving the right way the partitions to allocate all your free space. :)

---

