---
title: "contiguous free space"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by jimw on 2008-12-03
My understanding is that if I work from my 8.10 disk, using the 'contiguous free space' option, I can slip the OS into some of the 17 free Gigs I've got.  Is this correct?

Second question, if not enough of that space is contiguous, is there any method of putting stuff together such that I end up with enough space in one cluster?

Thanks

JimW

---

### Post by Happypants on 2008-12-03
Your question's a bit vague I have to say.  If you're looking to install with Windows on your system then you should first defrag (that's what I'm guessing you're asking about).  

Before you can install the OS you'll need to create a partition for it.  This can be done during the actual install or before using tools like Gparted.

---

### Post by Telescope_Nerd on 2008-12-03
There is quite a good tool for intalling ubuntu on a windows machine without physically partitioning your hard drive now called wubi

[http://wubi-installer.org/](http://wubi-installer.org/)

It seem's quite good I have two dual-booted machines one with a partition and one with wubi. I notice no difference in performance and it is certainly very easy to set up
T

---

### Post by jimw on 2008-12-03
Thanks for the answers.  However, I am not running a dual-boot system.

JimW

---

### Post by Happypants on 2008-12-03
> **jimw said:**
> Thanks for the answers.  However, I am not running a dual-boot system.

JimW

Then what exactly are you doing?  Installing Ubuntu on a system with data, but no OS?  Or on a clean system?

---

### Post by jimw on 2008-12-03
> **Happypants said:**
> Then what exactly are you doing?  Installing Ubuntu on a system with data, but no OS?  Or on a clean system?

I'm installing it on a system that already has 8.04 on it.

JimW

---

### Post by littlebat on 2008-12-03
You can install system into Vmware or VirtualBox to verify what is "contiguous free space". I have never installed system using this option but using manual option. 

"contiguous free space", is it the contigous free space in one partition? is it the contigous free partitions in hard disks? Anyone has tried this option can answer this question.

---

### Post by Happypants on 2008-12-03
I installed using the "contiguous free space" option last time I put Ubuntu on a machine (didn't really feel like messing around with partitioning).  It seems to just take the free space from the partition you create and not from any others.

---

### Post by jimw on 2008-12-04
> **Happypants said:**
> I installed using the "contiguous free space" option last time I put Ubuntu on a machine (didn't really feel like messing around with partitioning).  It seems to just take the free space from the partition you create and not from any others.

OK, yesterday evening I put in the Ibex Live CD and partitioned the disk, without touching the places where my data is.  Unfortunately, trying to install Intrepid Ibex in that new partition ended up with a message telling me that I had to go back to the Partitioning program and set up a root section in that new partition.

I put the live CD in again, and pressed the appropriate keys to set up that boot section.  I then went and tried to install again, with the same result, "you need to set up a boot section in that partition."

Does anyone know what I might be doing wrong?

Alternately, can I transfer all the data over to the new partition, and install Intrepid in the old partition?  The old partition, having already got Hardy Heron in it, should have a boot section, right?

Thanks,

JimW

---

### Post by Happypants on 2008-12-04
> **jimw said:**
> OK, yesterday evening I put in the Ibex Live CD and partitioned the disk, without touching the places where my data is.  Unfortunately, trying to install Intrepid Ibex in that new partition ended up with a message telling me that I had to go back to the Partitioning program and set up a root section in that new partition.

I put the live CD in again, and pressed the appropriate keys to set up that boot section.  I then went and tried to install again, with the same result, "you need to set up a boot section in that partition."

Does anyone know what I might be doing wrong?

Alternately, can I transfer all the data over to the new partition, and install Intrepid in the old partition?  The old partition, having already got Hardy Heron in it, should have a boot section, right?

Thanks,

JimW

Ok... Do me one quick favor.  Can you post up the read out of your fdisk -l for me?  It'll help me get a better grasp of exactly what's going on.

---

### Post by jimw on 2008-12-04
> **Happypants said:**
> Ok... Do me one quick favor.  Can you post up the read out of your fdisk -l for me?  It'll help me get a better grasp of exactly what's going on.

jimw@jimw:~$ fdisk -l
Warning: Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Error: Unable to open /dev/scd1 - unrecognised disk label.

jimw

---

### Post by Happypants on 2008-12-05
> **jimw said:**
> jimw@jimw:~$ fdisk -l
Warning: Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Error: Unable to open /dev/scd1 - unrecognised disk label.

jimw

Try ```
apt-get install build-essential
```

and see if you it actually gives you data when you run that again.

---

### Post by jimw on 2008-12-05
> **Happypants said:**
> Try ```
apt-get install build-essential
```

and see if you it actually gives you data when you run that again.

What I get is this:

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages

JimW

---

