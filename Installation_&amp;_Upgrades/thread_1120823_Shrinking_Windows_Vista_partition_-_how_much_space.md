---
title: "Shrinking Windows Vista partition - how much space"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by ilangocal on 2009-04-09
Hi
I would like to install Ubuntu or Kubuntu on my Acer Laptop machine that is currently running Windows Vista Home Edition.
Previously I did post a question on these forums with the same problem. I was told to shrink the Vista partition. (I was told that I might want to keep Windows Vista, which I think is a sensible idea)
Now, I have two partitions. I have a 160 Gb hardrive and 2Gb RAM. There are two drive currently. One is C: - this has only 26.9 free of 70 Gb. There is a Data Drive (D:) and has about 70 GB. How would I exercise the option of shrinking the partition?
Is it possible to shrink the 70 GB Vista Partition to 50 GB and use the remaining 20 GB for Ubuntu. Is that enough room for Ubuntu? Please advise me on my options.
I assume I cannot do anything to or on the D: drive as it is used for backup purposes or whatever.

Thanks in advance.

---

### Post by upchucky on 2009-04-09
yes, but you gotta read the partitoner instructions, as shrinking partitions only shrink from right to left, and windows puts stuff on a drive everywhere, gotta defrag it a couple of times first.

check the shrinking thing in the instructions cause i could have it backwards, it has to do with where the partitions are on the drive that dictates where stuff is moved to and from.

and lastly if a partition is moved or added/deleted after Ubuntu is installed, the grub bootloader will need to be redone so it knows where the partitions now are.

---

### Post by coffeecat on 2009-04-09
If you shrink the Vista partition by 20GB, that might not give Vista much elbow room for restore points and all the other accumulated stuff that Windows collects. Personally, I'd only shrink it 15GB max. So long as you keep all your personal data on the D: partition, 15GB is more than enough for all the Linux applications (except games) that you're likely to want. When you run the installer, you can designate a mount point for the data partition (if you select 'manual' at the partitioning stage) and the installer will set up an entry in /etc/fstab for you so that the data partition gets mounted at boot time. Then all you have to do is set up symlinks from your home folder to the folders in the data partition and you won't have to keep personal files on your Linux root partition.

Also - if you want to shrink the Vista partition, do so with the little utility inbuilt to Vista - it's much safer and you might not need to defrag. I can't remember exactly where you find it, but I know you start somewhere down the bottom left of the screen. :wink:

---

### Post by Mark Phelps on 2009-04-09
Don't be surprised when you use the Vista Disk Management utility to shrink the Vista partition, if you find it will allow very little shrinkage.

The following link contains things you can to do try and improve that:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

But if this is not enough, unless you have a Vist DVD lying around, I would advise against using the Ubuntu installer or GParted to shrink it further.  Both of those run a risk of corrupting the Vista partition, in which case, you would then have to boot from the Vista DVD and run Startup Repair to get Vista to boot again.

---

### Post by ilangocal on 2009-04-09
Thanks very much for all your replies.

After reading through your replies, I have come up some concerns:

1) The Vista Shrink Utility and its limitations
2) My limited space on C:

I have been thinking if I should consider loading Ubuntu on my Dell Laptop (This has 1GB of RAM on it and runs on an 1.66 GHZ Intel Pentium processor) that runs Windows XP Home Edition. This laptop has an 50 GB C: drive on it. There is another drive G: but I have no information on it. (not sure if that is a partition because when I try to find out what its size i am told that Used Space is 0 bytes and Free space is 0).

 My thinking is to get rid of Windows XP and set up only Ubuntu on it. 

In this case, what could be a recommended approach?

Thanks again.

---

### Post by coffeecat on 2009-04-09
> **ilangocal said:**
> I have been thinking if I should consider loading Ubuntu on my Dell Laptop (This has 1GB of RAM on it and runs on an 1.66 GHZ Intel Pentium processor) that runs Windows XP Home Edition. This laptop has an 50 GB C: drive on it. There is another drive G: but I have no information on it. (not sure if that is a partition because when I try to find out what its size i am told that Used Space is 0 bytes and Free space is 0).

My thinking is to get rid of Windows XP and set up only Ubuntu on it. 

In this case, what could be a recommended approach?

In order to find out what the real partition layout is, rather than what Windows tells you, simply boot up from the live desktop Ubuntu CD and go to System > Administration > Partitition Editor. By running the live CD you'll also get the opportunity to test all the Dell hardware before you commit yourself to an install. In particular, check to see if you can get the wireless to work. If it doesn't, and you need help, open a terminal, start a new help thread and post the output of 'lspci' so that we can see what the wireless chipset is.

If you really want to zap Windows XP when you install (and who could blame you? :wink: ) and use the whole HD for Ubuntu, start the installer and when you get to the partitioning stage, choose "Guided - use entire disc".

---

