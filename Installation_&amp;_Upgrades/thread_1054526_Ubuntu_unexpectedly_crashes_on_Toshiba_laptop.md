---
title: "Ubuntu unexpectedly crashes on Toshiba laptop"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by solomonhomicz on 2009-01-29
I'm trying to install 8.10 but it crashes a few minutes into installation, it also crashes a few minutes into running the live cd.
I previously installed 8.04 which worked fine for about a week then started crashing unexpectedly.
Toshiba Satellite M35X-S149, Intel Celeron M, 160g samsung HD, 60g Windows XP, 50g OpenSolaris 2008.11, and 50g free space.

I'm an engineering student and I want a Linux system on my laptop.
I really like Ubuntu (I've been running 8.04) in VirtualBox for some time now - I'd really like to let it out of the box - any suggestions welcome.

---

### Post by solomonhomicz on 2009-01-30
Just tried installing ubuntu with wubi, it installed but when I went to boot up it suddenly crashed. 
OpenSolaris runs beautifully, I'm heading over to their forum now to see if I can get help porting a Debian package that has the modem driver I need for my dial-up at home.
I have posted a few times with this problem before, why does the power just suddenly shut off when I try to run ubuntu?
Is their anybody with any ideas?

---

### Post by tommcd on 2009-01-30
> **solomonhomicz said:**
> Just tried installing ubuntu with wubi, it installed but when I went to boot up it suddenly crashed. 


Have you tried doing a real install? 
That is, boot the Ubuntu 8.10 (latest version) live CD and click the install icon. You will need to create (at least) 2 partitions (one for root and a smaller one for swap) and then install Ubuntu to the root partition.

EDIT: If running the live CD crashes, you may have better luck installing from the alternate install CD. This is a text based install that will provide the most fail safe environment for installing Ubuntu.

---

### Post by solomonhomicz on 2009-01-30
> **tommcd said:**
> Have you tried doing a real install?


I did a full install of 8.04 a couple of months ago, this worked fine for about a week.

Shortly after I installed the Debian package sl-modem-daemon I began to have unexpected crashes (all power off instantly).

The more I used it the more it crashed to the point of being unusable.

I obtained the live cd of 8.10, it crashed during install, so I tried wubi, it seemed to install fine but crashed on reboot (same thing - power off instantly).

Other things I've noticed:
The battery charge light comes on about two seconds before a crash.
Runs fine in VirtualBox.
OpenSolaris runs fine (has been installed for about a month now).

tommcd, there is an alternate install cd? I'll check it out, any info appreciated.

---

### Post by avtolle on 2009-01-30
[http://www.ubuntu.com/getubuntu/releasenotes/810#System%20lock-ups%20with%20Intel%204965%20wireless](http://www.ubuntu.com/getubuntu/releasenotes/810#System%20lock-ups%20with%20Intel%204965%20wireless) Does this apply to your system?

---

### Post by solomonhomicz on 2009-01-31
avtolle, thanks for the direction, I think this might be it.

I have the Atheros 5004G wireless, had a hell of a time getting it to work on 8.04, installing wifi radar finally got it working, after which the sudden crashes became unbearable.

However, the crashes first started after installing sl-modem-daemon,...,.deb to get my modem working.

They just got drastically worse after getting the wifi to work.

The wubi install of 8.10 crashed immediately after the initial reboot, the only thing I had a chance to do was click on the available wifi network.

There definitely seems to be a connection between any sort of network connection ;) and the crashes.

I'll look into using the linux-backports-modules-intrepid on a fresh install.

I'll try the live cd again, the wubi install went off without a hitch last time, but if I do that I'll want to have my windows partition bigger because that's all it recognizes.

I don't know very much about partitioning, etc.

Right now I have a 60g partition with Windows (installed first), a 50g partition with OpenSolaris and 50g of free space.

Any suggestions for a good place to learn about partitioning?
Is it possible to resize the Windows partition to include the 50g of free space?

---

### Post by tommcd on 2009-01-31
> **solomonhomicz said:**
> 
Right now I have a 60g partition with Windows (installed first), a 50g partition with OpenSolaris and 50g of free space.

Any suggestions for a good place to learn about partitioning?
Is it possible to resize the Windows partition to include the 50g of free space?
Here is a good basic tutorial on partitioning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
There is not much you really need to know about partitioning. An ideal, and simple, partitioning scheme involves creating 3 partitions for Ubuntu:
1. A root partition (10-12 GB if you have the space. You could go with less if space is limited. My Ubuntu root partition on my laptop is currently only using 3GB of a 10GB partition.  There are more elaborate partitioning schemes some people use; but these 3 partitions will work well for most users.
2. A swap partition of about 1GB. It could be less if you have a lot of memory.
3. A home partition for your data. This is whatever is left. It can be as big as you need it to be.

You could use the GParted live CD to partition your drive and shrink or expand partitions:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
If the 50GB free space is not next to the Windows partition on the disk you may not be able to expand Windows to include that space. Boot up the GParted live CD and check it out.

---

### Post by Zom-b on 2009-02-01
I gave up and just formatted and reinstalled, wish me well guys

---

### Post by solomonhomicz on 2009-02-01
Thanks for the pointers, tommcd, I'll definitely look into it in the next couple of day, GParted Live looks interesting.

I've tried installing from the live cd again, same thing, sudden crash.

I'm going to try a small wubi install and then install from the live cd linux-backports-modules-intrepid, before I try establishing my first network connection.

If this experiment is successful then I'll probably just wipe out OpenSolaris, resize Windows, and then do a larger wubi install.

If it's not successful then I'll look into the alternative install cd.

I'll be busy for the next few days, but I'll post back with results.

---

