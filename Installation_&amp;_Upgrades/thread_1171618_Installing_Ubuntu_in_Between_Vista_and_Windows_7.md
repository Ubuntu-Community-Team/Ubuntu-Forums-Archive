---
title: "Installing Ubuntu in Between Vista and Windows 7?"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Jdanniel on 2009-05-27
Hi everyone.

I'm new to Ubuntu, and have never installed it before.  I've dabbled with the Live CD, but that's about it.

May I please ask a question about putting Ubuntu on a dual boot setup?

Right now, I have Vista and Windows 7 RC installed on my computer.

The way the partitions are set up, Vista is on the main partition, and Windows 7 RC is on a smaller partition.  The hard drive is 300 GB and it's set up like this (in round figures):

Vista:  275 GB
Windows 7:  25 GB

The important point is:  Windows 7's partition is close to full, so I can't break space off of it for anything else.

With that in mind...

I would like to know the most practical way to install Ubuntu on my setup the way it is.  I used the partition manager in Vista to break off a 10 GB chunk of space for Ubuntu, but that space rests in between Vista and Windows 7.

When I tried installing Ubuntu, I got confused, since I've never done it before, and couldn't figure out how to use the middle partition for Linux.

So, I deleted that partition and gave it back to Vista.

Is there a way for me to get Linux installed on the system, using only space from the Vista partition, and without touching the Windows 7 partition?

Thank you very much for any assistance.  J. Danniel

---

### Post by hal8000 on 2009-05-27
One thing for sure is that your Windows 7 will break pretty soon if you have less than 10% free HD space, it wonnt be any different to ms previous releases so Id get some of your files backed up.

Use windows vista to shrink the partition if thats what youre used to.

When you install with the Jaunty CD, choose the option install in free space, it will find the space created by shrinking your partition-  and its not where you think it is. Microsoft have never been good at writing operating systems, shrinking a partition will put the space at the end. If Vista was installed first, then it may be the first primary partition and could well be in the centre, if windows 7 was first then it may be the third partition.
The windows naming technology C drive, D drive tells you nothing. You dont know if C is the first or second primary partition.
Device naming in linux is much more logical,as you'll find out. You will also need to install the linux boot loader grub to the mbr so that you can boot Ubuntu.

When it comes to partitioning, the gparted installer is graphical, the longer sections on the graph will be your windows 7 and vista installs, hope that helps

---

### Post by Jdanniel on 2009-05-27
Thank you for the reply.  

Each of my partitions, including Windows 7, has been backed up via Acronis True Image. I also backup my e-mail daily, and any files I create myself are immediately backed up.

I have a follow-up question:   You said the following:

> When you install with the Jaunty CD, choose the option install in free space, it will find the space created by shrinking your partition- and its not where you think it is.

In addition to my hard drive, I have two external 500 GB hard drives.  Each is roughly half-full.

So...when Ubuntu prepares to install in free space, will it ignore the free external space and look only for free internal hard drive space, or will it pile all of the free space together?

Thank you!  Jd

---

### Post by wkulecz on 2009-05-28
My advice is add a second hard drive.  I installed Kubuntu 9.04 to a large disk with plenty of free space that had:

Win7 RC1 32-bit 250GB
Win7 RC1 64-bit 250GB
Free space 500GB

After the install the 2nd partition (64-bit) was corrupted in a weird way and while Win7 64-bit would boot it wouldn't do anything because "access denied" resulted from any operation on the boot drive!

I had to re-install Win-7 64-bit after reformating that partition with the Win7 installer.

Be careful! if you value what's on your drive.  Never trust backups unless you have verified with a trial restore to a new drive before deleting what you have backed up! -- another good reason to invest $50-100 in a second drive.

--wally

---

### Post by Mark Phelps on 2009-05-28
> **Jdanniel said:**
> In addition to my hard drive, I have two external 500 GB hard drives.  Each is roughly half-full.

So...when Ubuntu prepares to install in free space, will it ignore the free external space and look only for free internal hard drive space, or will it pile all of the free space together?

Thank you!  Jd
Safest bet would be to disconnect the external drives before you install Ubuntu, that way, the only free space it will see will be the one you intend to use.

---

