---
title: "Windows 7 RC &amp; Ubuntu 9.04 dual boot problems"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by kmarchionda on 2009-06-29
I've been trying for a while to get both Ubuntu 9.04 and Windows 7 RC7100 setup in a dual boot on one hard drive. What I have done is the following. I began the windows 7 install. I partitioned my hard drive with the first half set up as NTFS. I left the second half unformatted. Windows 7 by default makes a "System Reserved" partition of 100MB before my partition for windows 7. I beleive the system reserve would be /dev/sda1 and my windows partition is /dev/sda2. The install of windows works great. Now the problem.
 
When I begin the Ubuntu 9.04 install I have a major problem at the partitioner. Gparted is showing that I have no operating system installed and that the whole hard drive is unformatted. I know I have half of it formatted because I can reboot and get right into windows. 
 
I have also tried Ubuntu first, but no matter what I try with the Ubuntu install, the Windows 7 installer doesn't like the partition I give it and says it can't install. Basically with Ubunutu I tried leaving a partition unformatted for windows, and i also tried one formatted NTFS. The windows 7 installer said it could not install on either. Any ideas would be greatly appreciated. I have looked around online quite a bit, but no one seems to have a solid answer on how to set this up when having a problem like this. The closest I found was someone saying to install Ubuntu first, and create a partition for windows as NTFS. Everytime I tried that it gave the NTFS partition a tag that would not allow windows 7 to install on it. I'm out of ideas at this point and I think I'm rambling. Hope I explained the problem well and I'll answer any questions you may have. Thanks.
 
Karl

---

### Post by coffeecat on 2009-06-29
When I installed Windows 7 RC, I did so on a drive with a pre-existing 60GB NTFS sda1 partition for XP, and a number of logical partitions for already-installed Linux distros. I told the W7 installer to use the 60GB partition, but to reformat it. It did so and it installed OK and without the 100MB 'system reserved' partition that you and others have found.

Then I tried on my Vista/Ubuntu laptop. This had: sda1 = Windows recovery partition, sda2 = Vista, sda3 = NTFS shared data, sda4 = extended containing my Linux logical partitions. Again I told the W7 installer to reformat sda2 and it did so, successfully installing W7 to sda2, and again without a 'system reserved' partition. Of course, with both, I had to repair grub, but I ended up with Windows 7/Ubuntu multi-boots.

So the trick seems to be to offer the W7 installer a single NTFS partition, but to tell it to reformat before installing. Have you tried that? It sounds as though you tried to install directly to a NTFS partition created with Gparted. I believe there are certain 'enhancements' to the way Vista and W7 create NTFS filesystems. And since Gparted is saying that no operating system is intalled, I guess it's having problems with the partition table created by the W7 disc.

If you want to start over, try this. With Gparted on the live CD, create a new (MSDOS) partition table - this will effectively wipe everything on the disc. Then create just one NTFS partition (sda1) for W7. Now start up with the W7 installer and tell it to reformat the NTFS partition you've just created, and then install. Once you've got W7 up and running, use the W7 inbuilt partition tool to create any further NTFS partitions you might need - if you need. Then use the live Ubuntu CD to create Linux partitions and to install Ubuntu.

---

### Post by starcraft.man on 2009-06-29
Edit: Beaten by coffee, off to lunch.

---

### Post by kmarchionda on 2009-06-29
I beleive I did try reformatting in the Windows 7 installer.  I will try again right now and confirm the results.  It'll take me a little while to do it all, but I'll get back to you when I'm done.  Thanks for the tip.

---

### Post by presence1960 on 2009-06-29
if your ubuntu live cd is not recognizing the Windows 7 RC install on your HDD try the alternate text based installer. get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by kmarchionda on 2009-06-30
Ok, so last night I tried everything coffeecat said, but I still had no luck. I just took a look at the post by presence1960 and something in my head clicked. I'm not positive, but I think my disc for ubuntu 9.04 was downloaded for my amd 64bit system. Right now I'm trying to install on an intel core 2 duo system. I guess I never thought of it because the installer for ubuntu would start right up. I'm downloading the i386 version now and will give it a go shortly. If this is really what is going on I will feel like a dope.  I must have tried every other possible solution, but never thought twice about the install cd. I had used it before and knew it was good. I think the problem is that I used it on an AMD 64 system. I'll keep you posted, but thanks for getting things turning in my head.

---

### Post by presence1960 on 2009-06-30
the AMD64 is for 64bit systems including Intel. It just has the name AMD64 because AMD first rolled it out. It works on Intel 64bit processors. The i386 is 32 bit. The reason I suggested the alternate text based installer is others who had a similar problem as yours were successful using that. Download the 64 bit alternate text installer not the i386  version.

---

