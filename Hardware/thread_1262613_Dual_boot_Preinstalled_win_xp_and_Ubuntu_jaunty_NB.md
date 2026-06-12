---
title: "Dual boot Preinstalled win xp and Ubuntu jaunty NBR on a new EEE 1005"
date: 2009-09-10
forum: Hardware
---

### Post by deboopi on 2009-09-10
Hello,
I heard so much good about linux that I want to give it a try on my new netbook.
So first of all I installed the windows XP Home
Beccause of the necessity of a swap drive I did repartition the system
I left the two smaller partitions as they were but repartitioned the two biggest partitions
The primary C was split into a 50 and a 30 Gb partition
The primary D became a logical 50 and logical 30 gb because I could not make them primary when repartitioning.
I installed Ubuntu jaunty NBR on the second 50 gb partition with the second 30 Gb partition as swap.
Ubuntu runs well but I have problems booting up windows xp
When I boot windows it starts reinstalling win xp home from the hidden partition, reboot a second time and yes, it starts installing win xp home once more.
So I think the ubuntu multi os booter points to a wrong partition, 
how to solve this?
 
Regards

---

### Post by katoiam on 2009-09-18
first of all a 30gig swap partition sounds crazy! I have been told no bigger than twice your ram is what you should have(if any one can correct me on that please do!)
so when you get to the grub menu (the black menu after it boots up, where you choose ubuntu or windows) what are your options? Does it just give you a few lines of ubuntu and only one windows option, or are there 2 windows?
also do you know if you have a partition preinstalled with windows recovery on it? 
I have a aa1 which came with windoze preinstalled, I installed UNR and found that there was a partition for recovering windows, it apears on the grub menu as a vista something (cant remember at the moment what it says exactly) its before windows on the menu and if I choose it, it begins to do something like you said.
Dont know if its any help! good luck any way:P

---

