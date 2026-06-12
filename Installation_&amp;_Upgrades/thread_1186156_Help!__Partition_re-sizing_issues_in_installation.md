---
title: "Help!  Partition re-sizing issues in installation"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by creperum on 2009-06-13
Hello!  

I am trying to install Ubuntu alongside the Windows that is already installed on my new laptop.  The installer that came with my "live session thumb drive" had problems with the re-partitioning ("Partman failed with exit code 141", with a long list of stuff in /var/log/syslog), so I ran gparted.  I tried to shrink my Windows partition and add a couple of other partitions for use by Linux.  

The problem came when gparted tried to apply the changes.  The progress window came up, went quickly through the first checking and simulations steps, and then spent ten minutes on the step where it actually resizes the partition.  

I couldn't tell if it was actually doing anything, so eventually I cancelled it..... which may have been a mistake.  Gparted spent another 5-10 minutes scanning the drive, with no results; I closed it.  When trying to mount that partition, it didn't recognize it (unsurprisingly).  Upon rebooting, Windows could tell there was a problem with the drive, but fortunately seems to have fixed it back to its original state.  

How long should it take for gparted to resize a partition?  Should I just let it run longer?  Or is there some problem with my installer?  I could download & burn a new installation CD, I suppose....


(Hmmm, while I'm here.... There is one small partition at the beginning of the drive, called "Recovery," containing directories Autorn, boot, data, efi, sony,...   Does anyone know what these files are?  It looks like all the Windows system files (over 50GB! Holy crap!) are on the main partition, so I guess they're some sort of "bootable in an emergency" backup OS?  Can I delete this first partition, or use it for something else?  The computer is a Sony Vaio laptop.)

---

### Post by Partyboi2 on 2009-06-13
Hi, resizing partitions can take awhile depending on how much has to be moved. I would recommend letting gparted finishing the process.

---

### Post by merlinus on 2009-06-13
If you are running vista, then you need to use its disk management tool to shrink the partition.  Delete temp and other unneeded files, and defrag first, no matter which version you have.

That may be your problem...

Also, best not to mess with the recovery partition in case you need to reinstall windows.

---

### Post by creperum on 2009-06-13
> **merlinus said:**
> If you are running vista, then you need to use its disk management tool to shrink the partition.

Excellent!  Thanks very much, merlin.  

I did as you suggested (which was a bit of a challenge, given that my Windows is running in Japanese, which I don't really read), and it worked great.  I then booted the live session, set up new partitions in the new free space with gparted (which took 4 minutes to complete), and am about to start the installation.

Why is it necessary to use Vista's homegrown disk management tool to shrink its partition?  I found several on-line tutorials that suggested it's possible to use gparted, with no mention of incompatibilities. 

Thanks again!

---

### Post by Bucky Ball on 2009-06-13
The partition at the beginning is generally what used to come on the Recovery Disk with your computer. Now you need to make the disk yourself (it has Windows recovery tools and the OS in case you need to reinstall).

I personally made two copies of the recovery partition on my laptop when I got it (there should be manufacturer instructions telling you how to do this), deleted everything on the drive when I was installing Vista, then installed Vista, then Ubuntu after that.

Basically, I wiped the drive and started from scratch.

---

### Post by merlinus on 2009-06-13
@creperum

Online tutorials are one thing, and real life experience is another.  If you search through the forum, you will see that quite a few people ran into problems unless they used vista's disk management tool for shrinking its partition, rather than gparted.

xp has not presented the same problem.

Without wishing to create flame wars, microsoft's proprietary and monopolistic practices create difficulties for those who wish to run linux and open source alternatives.

I hope things are working out for you.  Keep us posted!

---

### Post by Bucky Ball on 2009-06-13
> **merlinus said:**
> Without wishing to create flame wars, microsoft's proprietary and monopolistic practices create difficulties for those who wish to run linux and open source alternatives.

No flames here. I completely agree and am pouring you a glass of champagne! The kind of practices you speak of have held back software development by a decade at least.

---

### Post by moe19790 on 2009-06-13
> **merlinus said:**
> @creperum


Without wishing to create flame wars, microsoft's proprietary and monopolistic practices create difficulties for those who wish to run linux and open source alternatives.

I am things are working out for you.  Keep us posted!


I Agree 100%

---

### Post by creperum on 2009-06-14
> **merlinus said:**
> 
Without wishing to create flame wars, microsoft's proprietary and monopolistic practices create difficulties for those who wish to run linux and open source alternatives.

Ha!  Very delicately stated. :)  And I agree with you entirely.  I was a Mac user for years, and only bought a PC when I learned one didn't need to run Windows on it; installed Debian, and and never looked back....  This time I decided to try setting up a dual-boot, just for the heck of it & because I have the drive space.  But I digress....

Oh, and I apologize if I seemed challenging.  I meant no offense -- I was just curious about the differing information from different sources.  I should remember that on-line tutorials aren't always accurate.  You're absolutely right, of course, about real-world experience.

About to start the installation.  I'll let you know how it goes.

---

### Post by creperum on 2009-06-15
Well, the installation is done, and it seems to have worked like a charm.  Installed Ubuntu on its proper partition, and the installer did all the work of setting up grub and everything, and I have successfully booted into both Ubuntu and Windows.  I commend whoever developed the installer; I was afraid setting up dual-booting would be a real challenge, and it was so easy!!  

Thanks for your help, everyone.

---

### Post by merlinus on 2009-06-15
Congratulations -- well done!  Happy ubuntuing.

---

