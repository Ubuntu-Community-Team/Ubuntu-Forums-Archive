---
title: "Partitioning"
date: 2008-09-04
forum: General Help
---

### Post by Null81 on 2008-09-04
Hi

well, i was thinking about partitioning my 55gb hard drive in half.

acording to the paragon hard drive partitioner i have 19gb of unformatted space and 39gb of free space.

what does this unformatted space mean?

also, if i was to install linux on a partitioned hard drive, what format, because i would still love to put windows stuff on it if i decide linux isnt right for me. 


any suggestions?

---

### Post by az on 2008-09-04
> **Null81 said:**
> Hi

well, i was thinking about partitioning my 55gb hard drive in half.

acording to the paragon hard drive partitioner i have 19gb of unformatted space and 39gb of free space.

what does this unformatted space mean?

also, if i was to install linux on a partitioned hard drive, what format, because i would still love to put windows stuff on it if i decide linux isnt right for me. 


any suggestions?

Are you sure it is reporting 19 GB of unpartitioned space of 19 MB?  Because your drive would not come from the factory partitioned that way.  

Partitioning your drive is different than formatting it.  To use half your drive with Ubuntu, just shrink the first partition and leave the rest as free space (unpartitioned).  The ubuntu installer will create the other two partitions and format them for you.  If you want to get rid of Ubuntu, you can reinstall the widows bootloader (repair it), then delete the Ubuntu partitions ,then extend the Windows partition to use the free space.

You can also keep the extra partition and use is as another drive.  But they partition type does not determine the format - the filesystem determines the format.  But don't worry about that.

---

### Post by zvacet on 2008-09-04
> what does this unformatted space mean?

It means that is free space,not partitioned.Defragment your Windows partition few times and then shrink it.Add some space to 19GB unallocated space and there you will install Ubuntu.Default Ubuntu format is ext3.You can also read [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") for more information about dual boot install.

---

### Post by Null81 on 2008-09-04
here is the screens


[[IMG]http://img511.imageshack.us/img511/9513/19gbya9.png[/IMG]](http://imageshack.us)
[[IMG]http://img511.imageshack.us/img511/9513/19gbya9.454ce5e3f7.jpg[/IMG]](http://g.imageshack.us/g.php?h=511&i=19gbya9.png)

[[IMG]http://img75.imageshack.us/img75/6905/idkll3.png[/IMG]](http://imageshack.us)
[[IMG]http://img75.imageshack.us/img75/6905/idkll3.a441ecc31c.jpg[/IMG]](http://g.imageshack.us/g.php?h=75&i=idkll3.png)

---

### Post by Null81 on 2008-09-04
so any suggestions?

---

### Post by Null81 on 2008-09-04
=o

---

### Post by Pro-reason on 2008-09-04
> **Null81 said:**
> =o

I take it that the big red circle and the question marks mean you don't know what type of filesystem to use for the new partition.

But Zvacet had already told you that &#8220;ext3&#8221; is the filesystem for Ubuntu.

P.S. What operating system is that?  Vista with a theme?

---

### Post by Null81 on 2008-09-04
> **Pro-reason said:**
> I take it that the big red circle and the question marks mean you don't know what type of filesystem to use for the new partition.

But Zvacet had already told you that “ext3” is the filesystem for Ubuntu.

P.S. What operating system is that?  Vista with a theme?

xp with a theme

also, the thing is is that it says its Linux ext3 so i might not be able to store my files on it, as i do not know i backtrack on this.

---

### Post by Gannon8 on 2008-09-04
If you are installing ubuntu, then ignore that message (Though if you are using XP, you should be using GParted from the livecd). If you are not, NTFS would be better for storage under Windows.

PS Where do you get themes for WinXP?

---

### Post by Null81 on 2008-09-04
no i want to install something maybe other than ubuntu. i want something that is all purpose, like if i needed to switch out an OS or something i could have this available

Also i dont have a cd burner, i have to install everything with Unetbootin or Wubi. 






[www.deviantart.com](www.deviantart.com) for themes

---

### Post by Pro-reason on 2008-09-04
> **Null81 said:**
> xp with a theme

also, the thing is is that it says its Linux ext3 so i might not be able to store my files on it, as i do not know i backtrack on this.

You're worried about being able to access your files from either operating system?

You should have three partitions: one for your Windows installation, one for your Ubuntu installation, and one for your file storage. 

The Windows partition should be left as NTFS.  The Ubuntu partition should normally be ext3, but reiserfs is also good.

The storage partition should have a filesystem that both OSs can read.  Essentially you have a choice between FAT (16 or 32) and ext (2 or 3).  FAT partitions can be read by any system, but they're a bit crappy, and get fragmented.  Ext partitions are perfect for Linux, and they can be made to work on Windows by simply [installing drivers for them]("http://www.fs-driver.org/").

Basically, I would advise you to make your storage partition ext if you will be mainly using Ubuntu, and FAT if you will mainly be using XP.

Some people advise the use of NTFS for storage partitions, but Linux does not support NTFS 100%, and you can get mounting errors with it.

---

### Post by Gannon8 on 2008-09-04
If you are installing a Linux Distro, format it as ext3. For Windows, use NTFS.

PS Thanks for the themes :)

---

### Post by Null81 on 2008-09-04
hmmm...

well this isnt just my cpu, my mom wants at least half of this space. 

and it says these changes are irreversible, so this leads me to believe i need to make a good choice.


scenario.

i install sabayon on the ext3 partition, i decide i hate sabayon.

i am worried that i will have 20+gb of space i cannot use.

---

### Post by Null81 on 2008-09-04
> **Gannon8 said:**
> If you are installing a Linux Distro, format it as ext3. For Windows, use NTFS.

PS Thanks for the themes :)

np

---

### Post by AndyCee on 2008-09-04
> **Null81 said:**
> hmmm...

well this isnt just my cpu, my mom wants at least half of this space. 

and it says these changes are irreversible, so this leads me to believe i need to make a good choice.


scenario.

i install sabayon on the ext3 partition, i decide i hate sabayon.

i am worried that i will have 20+gb of space i cannot use.

'Irreversible' here means that data overwritten by the change made by the partition cannot be recovered by normal means. You can always install another OS within in the partition, or alter the partition itself.

So:
you make a new ext3 partition
you install sabayon in ext3 partition, decide you hate sabayon
you install Gentoo in ext3 partition, decide you hate Gentoo
you install ubuntu in ext3 partition, decide you want to marry it
you get a new computer, decide to return the disk space to windows for your mum

All here is possible
etc.

---

### Post by Null81 on 2008-09-04
hmm. i see. 

alright, you sold me. 

How big should i make this partition?

---

### Post by zvacet on 2008-09-05
In your first post you said that you want to partition HD in half.That means that you want to give 22-23GB of space.In that case 

1. root = 8-10GB                     mountpoint /
2. swap = 2xRam ( not allways in case you have 2GB or more 1-2 GB is enough)
3. home = rest of free space         mountpoint /home

---

