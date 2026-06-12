---
title: "gparted won't recognize other partitions"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by irisblaze on 2009-05-29
Hello,

I am trying to install ubuntu 9.04 on a 320GB sata HD (/dev/sda) this already has partitions for my work, music, windows, plus a 2GB swap and 80GB ext3 that i had ubuntu 8.10 on it... but gparted insists to take all the HD to install ubuntu 9.04 :(

fdisk -l shows my partitions correctly and i mounted them successfully but still gparted wanna be a pain about it... 

anyone can help me to get around this? thank you

---

### Post by kestrel1 on 2009-05-29
I assume that you have gone in to the custom partition side of gparted during the install.

---

### Post by raymondh on 2009-05-29
> **irisblaze said:**
> Hello,

I am trying to install ubuntu 9.04 on a 320GB sata HD (/dev/sda) this already has partitions for my work, music, windows, plus a 2GB swap and 80GB ext3 that i had ubuntu 8.10 on it... but gparted insists to take all the HD to install ubuntu 9.04 :(

fdisk -l shows my partitions correctly and i mounted them successfully but still gparted wanna be a pain about it... 

anyone can help me to get around this? thank you

Hi,

It could be that you have run into the max 4-partition rule.  If so, you would have to decide and delete/open up one partition.  can you post the output of
```

sudo fdisk -l
```

and if possible, take a screenshot of gparted and post as well.

EDIT : you may have already decided to install over the 8.10.  

Thanks,

---

### Post by irisblaze on 2009-05-29
@kestrel nice name, i think i read it in one of the night world novels... anyway i tried all possible screens... and none of them lists my other partitions

@raymond there you go in attachments

---

### Post by kestrel1 on 2009-05-29
From looking at the screen shot I think Raymond is correct. Unless some of your partitions are logical, you are way over the four primary partitions rule. How you have managed this I am unsure though.

---

### Post by raymondh on 2009-05-29
> **irisblaze said:**
> @kestrel nice name, i think i read it in one of the night world novels... anyway i tried all possible screens... and none of them lists my other partitions

@raymond there you go in attachments

Hi,

Am I counting 5 partitions?  I may be wrong.

Also, you may be trying to work on/install on a partition that is mounted...and Gparted will grey out the menu bar, if that were the case. You'll need to unmount.  Are you using gparted from the linux install you have?  Can you download gparted and burn to disk (it's a handy tool to have in a disc, anyways :)  )

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Keep us posted.

EDIT : I think I'm wrong re partitions as sda3 to sda9 all fall within the start and end blocks of sda2 hence Im thinking they're all logicals within the extended.

try unmounting.

---

### Post by irisblaze on 2009-05-29
> **kestrel1 said:**
> From looking at the screen shot I think Raymond is correct. Unless some of your partitions are logical, you are way over the four primary partitions rule. How you have managed this I am unsure though.

they are all logical except /dev/sda1... and let's say it's the 4max partitions rule, is there away to install Ubuntu or any other distro to my ext3 partition? I can't back up about 150GB of valuable data on DVDs

---

### Post by raymondh on 2009-05-29
> **irisblaze said:**
> is there away to install Ubuntu or any other distro to my ext3 partition? 

Sure ... keeping it logical as you have now.  Remember though that you are limited by the device number allocations ... see the gparted faq in the link I provided earlier.

---

### Post by raymondh on 2009-05-29
> **raymondhenson said:**
> Sure ... keeping it logical as you have now.  Remember though that you are limited by the device number allocations ... see the gparted faq in the link I provided earlier.

Want to triple-boot?  You still can. :)

---

### Post by kestrel1 on 2009-05-29
As Raymond says you need to make sure that you do not have any partitions mounted at the time. Installing on a logical partition is fine. Gparted is an excelent tool normally, so I can only imagine that you have partitions mounted.
Instead of running the live CD, just go straight for the install Ubuntu option. That way partitions are not mounted & you are not able to mount them prior to installation.

---

### Post by kestrel1 on 2009-05-29
> **raymondhenson said:**
> Want to triple-boot?  You still can. :)
I have multi booted in the past. I think the max I ever had was 7 OSes, Windows & Linux. I tend to use VirtualBox now though.:p

---

### Post by irisblaze on 2009-05-29
i'll try installing from the cd instead the live cd, but anyway i am sure all of them are unmounted

---

### Post by raymondh on 2009-05-29
> **kestrel1 said:**
> I have multi booted in the past. I think the max I ever had was 7 OSes, Windows & Linux. I tend to use VirtualBox now though.:p

Me too ... I have played around with about 22 distros now ... much simpler, less GRUB isssues (specially when we're asking GRUB to talk to another bootloader i.e. Darwin)

Anyway, I digress ...... How goes, Irisblaze?

---

### Post by irisblaze on 2009-05-29
all I needed to do is delete the linux partition... O.o 

i find it weird

---

### Post by raymondh on 2009-05-29
> **irisblaze said:**
> all I needed to do is delete the linux partition... O.o 

i find it weird

can you post a gparted shot again?  Am curious as well.

Glad you have it going :)

---

