---
title: "Partitioning software incompatibilites"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-07-21
I recently enountered [siginificant incompatibilities]("http://forum.sysinternals.com/forum_posts.asp?TID=19713") using Partition Magic in Windows 2000 creating a dual boot Windows 2000/Ubuntu Linux system.

I realize that PM must not be used in Vista or Windows 7.

I am planning on having two Windows 7 systems as follows:

1. Dual boot Windows XP Pro/Windows 7 Pro.
2. Dual boot Windows Vista Home Premium/Windows 7 Home.

For the XP system, I could format the partitionss using Partition Magic, run from XP, but if I later wish to add a Linux partition. I'd likely have the same problem I desctibed in the link supra.

For the Vista system, I could format the partitions using Acronis Disk Director 10, run from Vista. Again, this might be complicated by using Disk Director, I do not yet know.

So, what partitioning software is required for the following cases:

1. Dual boot XP/Windows 7
2. Dual boot Vista/Windows 7
3. Triple-boot XP/Windows 7/Ubuntu Linux.
4. Triple boot Vista/Windows 7/Ubuntu Linux

I am asking this same question in a Vista and in a Windows 7 forum.

---

### Post by eternalsword on 2009-07-22
gparted should be fine.  they have a live cd also by the way.  I would also recommend installing grub to a separate boot partition rather than overwriting the Master Boot Record (MBR).  

From your other thread, The EPBR stands for Extended Partition Boot Record, which tells how to boot logical partitions within the extended partition.  Since you asked the ubie installer for four new partitions, which is more than an msdos partition table can handle, it had to create an extended partition with the four partitions you asked for created as logical partitions.  

My guess is that a bug in Partition Magic caused it to not understand the boot codes gparted used in the EPBR and so couldn't load anything from the extended partition correctly.  

As to why you had an issue with the swap size/unallocated space.  You'd probably see the same thing with gparted if you asked it to round to the nearest cylinders.

EDIT:
with the MBR left in tact, you can use Window's own boot sequence to load either windows or grub.  I think you'll have less problems with dual-booting Vista/Win7 with linux that way, though it may take a little more time to set up.  I can't remember specifics on how to set it up, so I'll leave that to you to find out.

---

### Post by running_rabbit07 on 2009-07-22
...

---

### Post by raymondh on 2009-07-22
I'd use windows' disk managegement tool to touch/create partitions in/for windows. As 

I'd use Gparted for everything else.

---

### Post by Howard Kaikow on 2009-07-22
> **eternalsword said:**
> gparted should be fine.  they have a live cd also by the way.  I would also recommend installing grub to a separate boot partition rather than overwriting the Master Boot Record (MBR).

When I installed ubie 7.04 2 years ago to create a multiboot windows/linux system, I used the windows NTLDR to manage things, so I copied the boot record to the C drive and messed with menu.lst, I'm in the midst of doing that for ubie 9.04.  

> **eternalsword said:**
> From your other thread, The EPBR stands for Extended Partition Boot Record, which tells how to boot logical partitions within the extended partition.  Since you asked the ubie installer for four new partitions, which is more than an msdos partition table can handle, it had to create an extended partition with the four partitions you asked for created as logical partitions.

Yes, but there's no reason why Partition Magic did not understand the partititios. Windows and Perfect disk had no trouble, just Partition Magic.  

> **eternalsword said:**
> My guess is that a bug in Partition Magic caused it to not understand the boot codes gparted used in the EPBR and so couldn't load anything from the extended partition correctly. 

Good guess. 

> **eternalsword said:**
> As to why you had an issue with the swap size/unallocated space.  You'd probably see the same thing with gparted if you asked it to round to the nearest cylinders.

I did not ask PM to round to a cylinder.
Perhaps, it was an option that I neglected to look for to turn off/on.

> **eternalsword said:**
> with the MBR left in tact, you can use Window's own boot sequence to load either windows or grub.  I think you'll have less problems with dual-booting Vista/Win7 with linux that way, though it may take a little more time to set up.  I can't remember specifics on how to set it up, so I'll leave that to you to find out.

I did that 2 years ago.
I should be able to repeat this year.

I guess the solution to this issue is to find which partition managers are compatible with Windows XP and Windows 7 and ubie, and which are compatible with Vista and Windows 7 and ubie.

I could then run the appropriate program from a CD, rather than installed in the OS.

PM is installed in the OS because that was the only way to partition USB drives using PM.

---

### Post by Howard Kaikow on 2009-07-22
> **raymondhenson said:**
> I'd use windows' disk managegement tool to touch/create partitions in/for windows. As 

I'd use Gparted for everything else.

My recollection is that in Windows 2000, you can create, but not resize/move partitions.

Maybe it's better in XP, and beyond?

---

### Post by eternalsword on 2009-07-22
gparted works fine resizing ntfs partitions, only issue is Windows Vista (not XP, not sure about Win7) doesn't like when the partition size changes and fails to boot, so you'll need the install disc to fix the booting issue.  The data will be intact.  I used this method to triple boot a mac with OS X, Vista, and Ubuntu since bootcamp only allows one partition break.  

Usually the best thing to do is to plan ahead.  If you think you're going to run triple boot at some point, go ahead and partition out the disk as if you were going to do so from the start, just use a couple of data partitions as filler that way you can still use it for storage until the point where you're ready to install another system.

---

### Post by duyibo on 2009-07-22
Hey guys! I&#8217;ve found a free 64 bit Windows partition manager by accident. I downloaded it and used it. This software was amazing and easy to use. The most important is that it is free here I would like to share it with you. Following are copied from the website:

Partition Wizard Home Edition is a free partition manager designed by MT Solution Ltd. It supports 32/64 bit Windows Operating System including Windows XP, Vista and Windows 7. Home users can perform complicated partition operations by using this powerful but free partition manager to manage their hard disk partition such as Resizing partitions, Copying partitions, Create partition, Delete partition, Format partition, Convert partition, Explore partition, Hide partition, Change drive letter, Set active partition and Partition Recovery.

Partition Wizard comes absolutely free for Home user and free of charge for business user. Home users, business users, system administrators can easily use this Windows based software to manage their disk partitions. Download it for free from [http://www.PartitionWizard.com](http://www.PartitionWizard.com) and enjoy the new technology and new experience of Partition Wizard.

More information at [http://www.partitionwizard.com](http://www.partitionwizard.com)

---

### Post by Howard Kaikow on 2009-07-22
> **eternalsword said:**
> gparted works fine resizing ntfs partitions, only issue is Windows Vista (not XP, not sure about Win7) doesn't like when the partition size changes and fails to boot, so you'll need the install disc to fix the booting issue.  The data will be intact.  I used this method to triple boot a mac with OS X, Vista, and Ubuntu since bootcamp only allows one partition break.  

Usually the best thing to do is to plan ahead.  If you think you're going to run triple boot at some point, go ahead and partition out the disk as if you were going to do so from the start, just use a couple of data partitions as filler that way you can still use it for storage until the point where you're ready to install another system.


THanx.

That is one of my concerns.

I purchased Acronis Disk Director 10 just for use with Vista, but hanot yet installed/used it.

I'll have to read the Disk Director manual, and ask this question in the Acronis Disk Director forum and the Vista forum.

Of course, Vista is on a notebook. I will be partitioning to install Windows 7 as dual boot.  Hopefully, there will be enough disk space to install ubie as well, but this will not happen before next year, so it would likly be version 10.4.

---

### Post by Howard Kaikow on 2009-07-22
> **duyibo said:**
> Hey guys! I’ve found a free 64 bit Windows partition manager by accident. I downloaded it and used it. This software was amazing and easy to use. The most important is that it is free here I would like to share it with you. Following are copied from the website:

Partition Wizard Home Edition is a free partition manager designed by MT Solution Ltd. It supports 32/64 bit Windows Operating System including Windows XP, Vista and Windows 7. Home users can perform complicated partition operations by using this powerful but free partition manager to manage their hard disk partition such as Resizing partitions, Copying partitions, Create partition, Delete partition, Format partition, Convert partition, Explore partition, Hide partition, Change drive letter, Set active partition and Partition Recovery.

Partition Wizard comes absolutely free for Home user and free of charge for business user. Home users, business users, system administrators can easily use this Windows based software to manage their disk partitions. Download it for free from [http://www.PartitionWizard.com](http://www.PartitionWizard.com) and enjoy the new technology and new experience of Partition Wizard.

More information at [http://www.partitionwizard.com](http://www.partitionwizard.com)

I do not see anythying at Partition Wizard web site that mentions the *ix partitions. Perhaps there is an installed manual? Did not find a downloadable manual.

---

### Post by cb2410 on 2009-07-22
> **Howard Kaikow said:**
> I recently enountered [siginificant incompatibilities]("http://forum.sysinternals.com/forum_posts.asp?TID=19713") using Partition Magic in Windows 2000 creating a dual boot Windows 2000/Ubuntu Linux system.

I realize that PM must not be used in Vista or Windows 7.

I am planning on having two Windows 7 systems as follows:

1. Dual boot Windows XP Pro/Windows 7 Pro.
2. Dual boot Windows Vista Home Premium/Windows 7 Home.

For the XP system, I could format the partitionss using Partition Magic, run from XP, but if I later wish to add a Linux partition. I'd likely have the same problem I desctibed in the link supra.

For the Vista system, I could format the partitions using Acronis Disk Director 10, run from Vista. Again, this might be complicated by using Disk Director, I do not yet know.

So, what partitioning software is required for the following cases:

1. Dual boot XP/Windows 7
2. Dual boot Vista/Windows 7
3. Triple-boot XP/Windows 7/Ubuntu Linux.
4. Triple boot Vista/Windows 7/Ubuntu Linux

I am asking this same question in a Vista and in a Windows 7 forum.

I use Acronis DDS under WinXP to create/manipulate/delete/manage partitions using the Bootable Media built by Acronis DDS. I now have 3 PS systems running and the answer to your question is simple

1.  Windows 7 
2. Windows 7
3. Windows 7 + Ubuntu (all versions)
4. Windows 7 + Ubuntu ( all versions)

:popcorn:

---

### Post by running_rabbit07 on 2009-07-22
> **Howard Kaikow said:**
> I do not see anythying at Partition Wizard web site that mentions the *ix partitions. Perhaps there is an installed manual? Did not find a downloadable manual.

Very few products do mention Linux because the user base isn't large enough as it is with Windows & OS X. Every peice of hardware I have had to buy says "compatible with Windows XP/Vista/7 and OS X." But, when I shop I have faith in Ubuntu/Linux systems to just work with the hardware and it does.

---

### Post by Howard Kaikow on 2009-07-22
> **running_rabbit07 said:**
> Very few products do mention Linux because the user base isn't large enough as it is with Windows & OS X. Every peice of hardware I have had to buy says "compatible with Windows XP/Vista/7 and OS X." But, when I shop I have faith in Ubuntu/Linux systems to just work with the hardware and it does.

Software is different, especially software that deals with partitions, its gotta state what it supports.

I've downloded Partition Wizard and will install later this week.
I'll let y'all know what I find out.

---

### Post by running_rabbit07 on 2009-07-22
Mr. Howard, Does Windows 7 come on a LiveCD? I have been wandering if MS would ever allow themselves to make one. Thanx.

---

### Post by Howard Kaikow on 2009-07-22
> **running_rabbit07 said:**
> Mr. Howard, Does Windows 7 come on a LiveCD? I have been wandering if MS would ever allow themselves to make one. Thanx.

I asked Mr. Howard.
He does not know.

---

### Post by Howard Kaikow on 2009-07-23
> **eternalsword said:**
> gparted should be fine.  they have a live cd also by the way.

Alas, GParted won't do.

There's a dire warning at the [GParted Live web site]("http://gparted.sourceforge.net/livecd.php") about a bug that allegedly affects some HP Pavilon computers. 

The bug is still under dicussion, so until resolved, I dare not use GParted on my notebook.

---

### Post by eternalsword on 2009-07-23
> **Howard Kaikow said:**
> Alas, GParted won't do.

There's a dire warning at the [GParted Live web site]("http://gparted.sourceforge.net/livecd.php") about a bug that allegedly affects some HP Pavilon computers. 

The bug is still under dicussion, so until resolved, I dare not use GParted on my notebook.

You could always run System->Administration->Partition Editor from an ubuntu live cd.

---

### Post by running_rabbit07 on 2009-07-23
> **eternalsword said:**
> You could always run System->Administration->Partition Editor from an ubuntu live cd.

I think that is the same program. When I installed GParted in Synaptic, the Partition Editor then appeared in the System->Administration menu.

---

