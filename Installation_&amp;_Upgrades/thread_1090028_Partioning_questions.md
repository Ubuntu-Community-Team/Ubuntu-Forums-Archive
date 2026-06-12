---
title: "Partioning questions"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by sjmcyyc1960 on 2009-03-07
Can someone explain to me how the partioner works in the install process, it seems no matter which option I choose the after graph shows it is going to use all of the drive. I set up an ext3 partition and a swap file thinking it would automatically install there, but when I choose the drive with the linux partitions I can see them in the top graph but in the after graph it shows all of the drive being used, can I force it to intall to the ext3 partition? Is there an easier way?

Thanks for the help

---

### Post by taurus on 2009-03-07
If you already have ext3 and swap partitions, you want to pick the Manual option at the partition screen.  Then on the next screen, mount the ext3 partition to / (root filesystem) and format it.  You probably don't have to do anything to the swap partition since the installer knows how to handle it.  Otherwise, mount that small partition to swap.

---

### Post by sjmcyyc1960 on 2009-03-07
Thanks Taurus, my big fear was seeing that graphical display at the top saying all the drive was going to be used, I was worried about hitting the next button in case it was going to format the whole drive...so this will not happen? By the way I did have manual selected but showed it was going to use the whole drive.

Thanks again, I would just like to confirm that I should select manual...do I have to select the drive from above that or just select manual and then next.

---

### Post by simtaalo on 2009-03-07
just select manual then next, then it will give you options on how you want to partition things.

---

### Post by gbswales on 2009-03-07
I just tried the install from the live CD and I am confused when it gets to the partitioner. This does not seem to show me what drives/partitions just the one bar that shows how ubuntu configuration will be set up - going to manual didnt help me much.

I want to be able to see exactly where linux will set up its partitions and to make sure that it doesnt reduce my windows partition more than it has to. I have one hard drive with a single partition (C) and a much bigger hard drive with two partitions (F) - Ideally I would prefer to mount the linux partition on F rather than C as I have more space there.

For now I have used WUBI to install but the problem with this is that while I can access the content on my second windows drive I cant access my documents etc on the C drive (preumably because it is running inside a file on that drive) 

how do i put Ubuntu where I want it and maintain dual booting and access all my drives? (preferably without any command line stuff!!!)

---

### Post by SonicSteve on 2009-03-10
The windows files are accessible under the root file system from the /host folder. I just confirmed this on my lone wubi installation. Places/computer/filesystem/host folder. 

by the way, over time you may find that the command line grows on you. There are times that it's nice to have. Like mounting an NTFS partition that needs to be forced. The error that the graphical mount gives, is basically a perfect cut and paste into the command line option. Yes there could a graphical force button but since there isn't the command line comes in really handy.

---

