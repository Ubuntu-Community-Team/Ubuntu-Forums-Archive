---
title: "How can i Optimize my system?"
date: 2008-06-05
forum: Hardware
---

### Post by MasterNetra on 2008-06-05
I want to know how can I optimize my system to go as fast as it can? From a software perspective. 

Its a labtop with a Intel Core 2 Duel processors, a 256mb  "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (VGA Compatible and can use OpenGL, not sure if the OS is utilizing it though.)" It also has 1GB of ram and a mere 80GB Hard drive. (If you need to know anything else about it let me know) 

Also... For whatever reason OS is eating my ram >.> leaving about 1/4 of it free atm. I only have Kinfo and Firefox 3 open. According to Kinfo about half of it is Disk Cache. Anyway I can get it to use swap for cache instead of having it waste Ram power?

Thanks in advance.

---

### Post by jrusso2 on 2008-06-05
> **MasterNetra said:**
> I want to know how can I optimize my system to go as fast as it can? From a software perspective. 

Its a labtop with a Intel Core 2 Duel processors, a 256mb  "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (VGA Compatible and can use OpenGL, not sure if the OS is utilizing it though.)" It also has 1GB of ram and a mere 80GB Hard drive. (If you need to know anything else about it let me know) 

Also... For whatever reason OS is eating my ram >.> leaving about 1/4 of it free atm. I only have Kinfo and Firefox 3 open. According to Kinfo about half of it is Disk Cache. Anyway I can get it to use swap for cache instead of having it waste Ram power?

Thanks in advance.

Ram is much faster then swap.. Its caching what it needs in your ram so its using it to load faster.  Unused ram is the wasted ram.

---

### Post by MasterNetra on 2008-06-05
> **jrusso2 said:**
> Ram is much faster then swap.. Its caching what it needs in your ram so its using it to load faster.  Unused ram is the wasted ram.
oh. Should I leave the unused alone though I noticed that the remaining useage is by Applications? (Not that i know how to change it anyway x.x)

---

### Post by jrusso2 on 2008-06-05
> **MasterNetra said:**
> oh. Should I leave the unused alone though I noticed that the remaining useage is by Applications? (Not that i know how to change it anyway x.x)

Its working as intended. The only way to optimize things would be to maybe shut down unneeded services but this would take a bit of expertise.

---

### Post by Chayak on 2008-06-05
Yes, Ubuntu uses about 150mb of ram for the system which is still very lean when compaired to say Vista.  You'll see most of the ram is used to cache frequently used programs and system files to speed up the system by not having to access the hard drive.

Optimizing a linux system can be quite an undertaking going from simply turning off services you don't use to recompiling your kernel specifically for your hardware with an optimized compiler and then recompiling the system software.  It's not an undertaking for someone new to linux.

The biggest bottleneck of most modern systems is the harddisk.  If you want to really speed up your system and keep a margin of saftey for your data get four identical hard drives and set them up using a raid card in raid 10.  You can do normal striped raid but every drive you add to it only increaces the chance that one fails and you loose the contents of the drives.  Though if you use two smaller drives in striped raid and a third larger drive to back up to it should mitigate the risk to a reasonable level.

---

### Post by HunterThomson on 2008-06-05
If you want to get nuts. You could build your own kernel with only the components needed to run your hardware.... OR you could build your own Debian OS and Kernel.

---

### Post by MasterNetra on 2008-06-05
> **jrusso2 said:**
> Its working as intended. The only way to optimize things would be to maybe shut down unneeded services but this would take a bit of expertise.

So what things could I do to ensure that my system is performing at its peak aside from Killing unnecessary tasks?

> **Chayak said:**
> Yes, Ubuntu uses about 150mb of ram for the system which is still very lean when compaired to say Vista.  You'll see most of the ram is used to cache frequently used programs and system files to speed up the system by not having to access the hard drive.

Optimizing a linux system can be quite an undertaking going from simply turning off services you don't use to recompiling your kernel specifically for your hardware with an optimized compiler and then recompiling the system software.  It's not an undertaking for someone new to linux.

The biggest bottleneck of most modern systems is the harddisk.  If you want to really speed up your system and keep a margin of saftey for your data get four identical hard drives and set them up using a raid card in raid 10.  You can do normal striped raid but every drive you add to it only increaces the chance that one fails and you loose the contents of the drives.  Though if you use two smaller drives in striped raid and a third larger drive to back up to it should mitigate the risk to a reasonable level.

For starters I'm using the sister distro Kubuntu. Second I don't have the money to spare for multiple Drives (or its components) and unless they connect via USB port multiple drives aren't doable for my LABTOP. Third what does having multiple small drives do for performance?

---

### Post by ChameleonDave on 2008-06-05
> **MasterNetra said:**
> Anyway I can get it to use swap for cache instead of having it waste Ram power?


You have things completely back-to-front.

You waste RAM by *not* using it.  The swap partition is a last resort when you run out of RAM.  In the ideal system, the swap is never ever touched.

The most optimised system is one that loads all your most commonly-used apps into RAM instead of having to get them from the hard drive every time.

---

### Post by lisati on 2008-06-05
My experience of video on a Windows system (if you'll pardon the "swearing") is that the more ram you have available for the job, the merrier. I'm still finding my way round editing using Ubuntu.

---

### Post by jrusso2 on 2008-06-05
> **MasterNetra said:**
> So what things could I do to ensure that my system is performing at its peak aside from Killing unnecessary tasks?



For starters I'm using the sister distro Kubuntu. Second I don't have the money to spare for multiple Drives (or its components) and unless they connect via USB port multiple drives aren't doable for my LABTOP. Third what does having multiple small drives do for performance?


Here is a page that talks about shutting down unneeded services

[http://ubuntulinuxhelp.com/a-quick-way-to-improve-ubuntu-linux-operating-speed-performance/](http://ubuntulinuxhelp.com/a-quick-way-to-improve-ubuntu-linux-operating-speed-performance/)

Becareful

---

### Post by MasterNetra on 2008-06-05
> **lisati said:**
> My experience of video on a Windows system (if you'll pardon the "swearing") is that the more ram you have available for the job, the merrier. I'm still finding my way round editing using Ubuntu.

Be nice to be able to use USB drives as ram like Vista can. I wonder if Ubuntu/Kubuntu will ever recieve that upgrade...

---

### Post by sonofusion82 on 2008-06-05
> **lisati said:**
> My experience of video on a Windows system (if you'll pardon the "swearing") is that the more ram you have available for the job, the merrier. I'm still finding my way round editing using Ubuntu.

yes, Linux works differently, having little free RAM doesn't mean it will be slow, it is just used by the system for caching and can be released to applications when necessary. paging stuff to swap will only slow things down. you probably know how the windows trashes when it pages less used memory to its page file.

don't worry, your Core 2 Duo and 1GB of RAM is plenty for Ubuntu.

like some of replies, if you really wanna go nuts about optimizing, try recompiling the kernel with custom configurations. but it is definitely not something easy.


@MasterNetra,
it might be possible to mount the swap drive on a USB flash drive, but I am not sure how it will work out.

---

### Post by lisati on 2008-06-05
> **sonofusion82 said:**
> 

don't worry, your Core 2 Duo and 1GB of RAM is plenty for Ubuntu.



Possible crossed message: I have a Celeron M in my Ubuntu box!!!

---

### Post by MasterNetra on 2008-06-05
I know there was a lag issue with Ubuntu 8.10, has it been fixed yet? I had initally installed Ubuntu (64-bit) but had some laging issues (64-bit sense my hardware runs 64 bit stuff..heck my labtop came with a 64bit version of windows XP)

---

### Post by Unix_Slayer on 2008-06-05
> **MasterNetra said:**
> Be nice to be able to use USB drives as ram like Vista can. I wonder if Ubuntu/Kubuntu will ever recieve that upgrade...

There will never be a readyboost for Linux. Don't need it. You can increase the size of your swap file, depending how much is being utilized by the system.

---

### Post by MasterNetra on 2008-06-05
Is that how Vista is using USB drives? As swap file?

(Question regarding Ubuntu's Lag still stands)

---

### Post by peakshysteria on 2008-06-05
What do you mean; lagging issues?

---

### Post by osx424242 on 2008-06-05
> **MasterNetra said:**
> So what things could I do to ensure that my system is performing at its peak aside from Killing unnecessary tasks

What makes you think that your system is *not* performing at its peak?  Are you just intellectually curious, are you jealous of your neighbor's computer ;), or do you have a specific issue that you are trying to address?

---

### Post by Unix_Slayer on 2008-06-05
> **MasterNetra said:**
> Is that how Vista is using USB drives? As swap file?

(Question regarding Ubuntu's Lag still stands)


Just about. You could actually say it was borrowed from Unix.

type this in terminal:

```
free -m
```


and see how much your swap file is using.

---

### Post by ChameleonDave on 2008-06-05
> **Unix_Slayer said:**
> There will never be a readyboost for Linux. Don't need it. You can increase the size of your swap file, depending how much is being utilized by the system.
You don't need it, but there is a hack that will enable it if you want to.

Just search for "ReadyBoost" on these fora and you'll find the how-to.

---

### Post by ilrudie on 2008-06-05
If you really want to use a USB drive as swap you can always use mkswap and swapon.  Its probably not a good idea unless your system is locked up because its out of swap space (if you only have one user and you aren't running large databases this probably wont happen).  swap space on a USB drive will generally be slower than swap on an internal disk which is much slower than ram.  That said if you REALLY need extra swap space run 'df' and see if there is free space on your internal disks first.  If there is just mkswap to make a swap file (rather than a swap device) on your internal disks.

Also not entirely sure what readyboost is but if its caching something on a thumb drive like I think it is that may be the worst idea I have ever.  I havn't really looked into thumb drive speeds today but last I checked they were much much slower than hard disks.

---

### Post by MasterNetra on 2008-06-05
> **osx424242 said:**
> What makes you think that your system is *not* performing at its peak?  Are you just intellectually curious, are you jealous of your neighbor's computer ;), or do you have a specific issue that you are trying to address?

Granted I'm not exactly sure if it isn't already. x.x But at the same time I don't know if the OS utilizes the hardware at a optimal level from install.

> **peakshysteria said:**
> What do you mean; lagging issues?
I mean i had downloaded Ubuntu (64-bit) shortly after it was released and burned it to cd. It ran many programs more slowly then Kubuntu here.

> **ilrudie said:**
> If you really want to use a USB drive as swap you can always use mkswap and swapon.  Its probably not a good idea unless your system is locked up because its out of swap space (if you only have one user and you aren't running large databases this probably wont happen).  swap space on a USB drive will generally be slower than swap on an internal disk which is much slower than ram.  That said if you REALLY need extra swap space run 'df' and see if there is free space on your internal disks first.  If there is just mkswap to make a swap file (rather than a swap device) on your internal disks.

Also not entirely sure what readyboost is but if its caching something on a thumb drive like I think it is that may be the worst idea I have ever.  I havn't really looked into thumb drive speeds today but last I checked they were much much slower than hard disks.

Well no, I had thought maybe that Vista was using USB Drives in a way that made them act like Ram. My swap space for all i know has been pretty much unused it seems...I think...then again I don't actually check when running a large game or app.

---

### Post by Chayak on 2008-06-05
> **MasterNetra said:**
> So what things could I do to ensure that my system is performing at its peak aside from Killing unnecessary tasks?



For starters I'm using the sister distro Kubuntu. Second I don't have the money to spare for multiple Drives (or its components) and unless they connect via USB port multiple drives aren't doable for my LABTOP. Third what does having multiple small drives do for performance?

Kubuntu/Ubuntu doesn't really matter as the system is the same except for the GUI running on it and it's associated software. It's all the same under the hood, just a different paint job.

To get the max performance from drives you have to get past the drive speed bottleneck.  The most common way to do this is to use multiple drives in whats called a striping array (Raid 0).  The system will essentially see both drives as one and write/read "stripes" of data to/from each.  This theoretically doubles the read/write speed of a single drive.  The downside of this is data is split on both drives and if one drive should fail there is no way to reconstruct the data on the other.  The fix to this is known as Raid 10 which is two sets of striped drives mirroring each other.  If one drive should fail the other set will take over until you replaced the failed drive.

As you're using a laptop there really isn't much you can do though I have heard about people using software raid with multiple usb drives. I can't say this will do much to help though.

---

### Post by MasterNetra on 2008-06-05
> **Chayak said:**
> Kubuntu/Ubuntu doesn't really matter as the system is the same except for the GUI running on it and it's associated software. It's all the same under the hood, just a different paint job.

To get the max performance from drives you have to get past the drive speed bottleneck.  The most common way to do this is to use multiple drives in whats called a striping array (Raid 0).  The system will essentially see both drives as one and write/read "stripes" of data to/from each.  This theoretically doubles the read/write speed of a single drive.  The downside of this is data is split on both drives and if one drive should fail there is no way to reconstruct the data on the other.  The fix to this is known as Raid 10 which is two sets of striped drives mirroring each other.  If one drive should fail the other set will take over until you replaced the failed drive.

As you're using a laptop there really isn't much you can do though I have heard about people using software raid with multiple usb drives. I can't say this will do much to help though.

I'll keep that in mind for future desktops.

---

### Post by sergiom99 on 2008-06-05
I have 2Gb RAM, can I only have 512Mb swap?

---

### Post by MasterNetra on 2008-06-05
> **sergiom99 said:**
> I have 2Gb RAM, can I only have 512Mb swap?

I suppose depends what you use it for. I hear you should have 2x as much swap as you do ram. Of course if your not a gamer or even use any major ram eating apps/games then i suppose you could get away with it.

---

### Post by sergiom99 on 2008-06-05
I knew that rule of thumb, but now I think I read somewhere that with large RAM, you could use less swap, that was for old systems with less than 1Gb, and now no matter how much RAM you have, its ok to have as much as 1Gb SWAP.

---

### Post by MasterNetra on 2008-06-05
I suppose you could. If it works for you then do it I would say :p But then again I'm still a beginner when it comes to linux :P

---

### Post by ChameleonDave on 2008-06-05
> **MasterNetra said:**
> 
Well no, I had thought maybe that Vista was using USB Drives in a way that made them act like Ram. 

Since "swap" means disk space used as virtual memory, there isn't really difference between using a USB drive to act like RAM (virtual memory) and using a USB drive to act as swap (virtual memory).

---

### Post by MasterNetra on 2008-06-05
> **ChameleonDave said:**
> Since "swap" means disk space used as virtual memory, there isn't really difference between using a USB drive to act like RAM (virtual memory) and using a USB drive to act as swap (virtual memory).

Well i figured there be little to no differance in using USB Drive for swap or using Hard Disk. I mean both need to be written to and read :p Of course I think USB drives are more prone to corruption. (especially if you yank it out when ya shouldn't XD)

---

### Post by ChameleonDave on 2008-06-05
> **MasterNetra said:**
> Well i figured there be little to no differance in using USB Drive for swap or using Hard Disk. 

The flash storage on a USB stick will have faster access than a hard disk, especially the older IDE hard disks.  Modern SATA disks are a bit faster.

However, a flash storage drive jutting out from a USB port is physically vulnerable, and flash storage can only support a certain number of writes before it fails.  It should still last a good, long time though.

Simply buying more RAM is almost certainly the best solution.

---

### Post by JcZndeR on 2008-06-05
sry to jump in here but i was just looking up stuff for my graphics card GeForce 6150SE nForce 430
and i was wondering wat is this "RenderAccel" thing they are talking about on here:
[http://gtkperf.sourceforge.net/index.php?page=testing&id=2](http://gtkperf.sourceforge.net/index.php?page=testing&id=2)
thanks :P

edit: i think it has something to do with optimization, yes?

---

### Post by MasterNetra on 2008-06-06
> **JcZndeR said:**
> sry to jump in here but i was just looking up stuff for my graphics card GeForce 6150SE nForce 430
and i was wondering wat is this "RenderAccel" thing they are talking about on here:
[http://gtkperf.sourceforge.net/index.php?page=testing&id=2](http://gtkperf.sourceforge.net/index.php?page=testing&id=2)
thanks :P

edit: i think it has something to do with optimization, yes?

Not with optimizing my system. Please create your own thread instead of trying to divert someone elses.

---

### Post by JcZndeR on 2008-06-06
alright, hey.. just asking.

---

### Post by MasterNetra on 2008-06-06
> **JcZndeR said:**
> alright, hey.. just asking.

I know but some people like myself don't like there question threads interrupted with something unrelated.

---

