---
title: "Upgrade problem with SATA RAID"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by d_e_monat on 2009-05-18
I have done a lot of searching and RTFM on this ;)

I have an Asus A8V-MX mobo with SATA.  I was successfully running Ubuntu 8.04 on RAID 0 (fake raid).  This took a lot of work and research, to get running, but it was a learning experience :)

Two days ago I performed a dist upgrade to 8.10.  I rebooted and got the <initramfs> prompt!  Uh oh!  I was able to "dmraid -ay" and continue the boot!

BTW:  The dist upgrade is step one of an upgrade to 9.04.

Here is the strange thing.  The upgrade wipes out the old kernels and initrd.img files and installs 2 new kernels.  The kernel version 2.6.24-24-generic will boot-up properly and the 2.6.27-14-generic will not!??!

I have tried to "update-initramfs" on the newer kernel (several times) without success!

Does anyone have an idea on what the heck is going on here?  

Also, since I have one of the kernels working OK, can I upgrade to 9.04 without problem? 

Thanx

---

### Post by RainKap on 2009-05-19
Hmm, it looks as though I'm not alone. I went through a similar process yesterday, upgrading my system (Tyan Thunder MoBo, 2 x Opteron dual core, WD Raptor 150GB for / and /home, 4 x Seagate Barracuda 320GB in a RAID5 array for bulk storage on /shared, all on the MoBo SATA ports) from 8.04. I left it to plough through the upgrade from 8.04 to 8.10 while we went out to a concert yesterday evening, then from 8.10 to 9.04 overnight. When I eventually restarted into 9.04 with kernel 2.6.28-12 this morning, it couldn't find the UUID for the md0 array.

mdadm --misc /dev/mdo reported "/dev/mdo: no such file or directory".

There are also other wrinkles: trying to start the terminal gave an error: "There was an error creating the child process for this terminal"; trying to remove redundant applications using Synaptic gave an error: "Error failed to fork pty".

I'd be prepared to regress to 8.04 (though that leaves the problem that Unison, which I use to sync between my laptop - now upgraded to 9.04... - and my desktop won't work, 'cos it has to have the same version of Unison at both ends) on the desktop, but I'm very wary of doing anything which would stop me getting access to the data on the RAID array. Can anyone offer any helpful suggestions on regaining access to the RAID array so I can copy it somewhere safe, purlease?

Thanks in advance

Ian

---

### Post by RainKap on 2009-05-19
Phew! After some more digging in the Ubuntu forums, I found this link: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298) which gives a work-around to let the md0 array be mounted. The files on my RAID array are now backed up to *two* other locations(!), and I think I'll probably do a fresh install of 9.04 to see if that sorts out the other wrinkles...

Ian

---

### Post by d_e_monat on 2009-05-19
Bravo RainKap.  I am still wallowing in 8.10 with kernel 2.6.24-24

I will check out that bug report however I  don't think it relates to my problem.:p

I am thinking of doing a Live CD install of 9.04. hoping it will build a correct initrd file.

---

