---
title: "Basic Question about Partitioning"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by selfnoise123 on 2006-01-08
I have a pretty basic question about setting up a dual boot with my system.  Here's my setup:

I have 2 NTFS partitions on a 160gb HD.  The 1st is the bootable partition and contains Windows 2000 Professional.  The 2nd is just some extra space, and is empty at the moment.  I would like to install Ubuntu Breezy on that 2nd partition.

So I boot the install CD for breezy, tell it to do manual partition, then delete the 2nd partition and tell Ubuntu to allocate the freed space.  It does so and creates a swap partition as well.  It also moves the bootable flag over to the new EXT3 partition, and says something about the 1st NTFS partition not being in use when I hit enter on it.

My question is, should it be moving the bootable flag over to the Ubuntu install?  I'm concerned about accidentally wiping out my Windows 2000 install while doing this.

---

### Post by reet on 2006-01-08
The Ubuntu manual partition setup will not wipe your NTFS windows partition unless you tell it to. What I think it is saying is that you have not set a mount point for the NTFS partition so it will be unaccessable in Ubuntu. Look at the options for the NTFS partition and set it's mount point to somewhere like /windows. The bootable flag is required on the EXT3 partition that will hold the Ubuntu installation.

Also note that NTFS partitions are read-only in Ubuntu.

---

### Post by Herman on 2006-01-08
Hello, selfnoise123, you asked:
>  should it be moving the bootable flag over to the Ubuntu install? I'm concerned about accidentally wiping out my Windows 2000 install while doing this. That sounds okay to me, the reason for that is that later on in your install, the Ubuntu installer will ask for your permisson to install the GRand Unified Bootloader, (GRUB), to the Master Boot Sector, or 'MBR', for short. 

Really it will just install a small part of GRUB to MBR to change the MBR to point to the partition that has the bootable flag. You want it to point to the new Ubuntu partition, because the most important part of the GRUB boot loader will be installed there. 
Then, when you are booting your computer, GRUB will give you a choice of which operating system you would like to boot into, and either point to the Ubuntu kernel, or point back to the old Windows chainloader that you are used to if you choose that at boot-up.
If you would to see some illustrations to check that you are on the right track, click my signature link and there are three illustrated examples of Ubuntu being installed dual boot with Windows.
I think your bootable flag being moved to Ubuntu is fine, but this part worries me:
>  and says something about the 1st NTFS partition not being in use when I hit enter on it. I don't know why it would be saying that, that part doesn't sound right. Are you sure about that?  Regards, (Herman):smile:

---

### Post by Sef on 2006-01-09
> My question is, should it be moving the bootable flag over to the Ubuntu install?

I kept my bootable flag on my Windows partition, and everything works fine.  It defaults into Ubuntu.

---

