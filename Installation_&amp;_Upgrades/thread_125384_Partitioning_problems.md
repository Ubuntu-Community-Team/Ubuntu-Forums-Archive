---
title: "Partitioning problems"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by erj80 on 2006-02-03
Hello,

I'm completely new to both Ubuntu and Linux, but have managed to install Ubuntu from CD-ROM to my IBM Thinkpad T30. I run Ubuntu as my only operating system and would just want to use a single partition for my 20 GB harddrive. 

The problem is that during the installation I didn't exactly know what too chose and now I'm having two (I think) partitions on my harddrive. This wouldn't be a great problem if it wasn't for the fact that Partition 5 (18,63 GB) is inaccssible and not formatted to any file system while Partition 1 seems to be working but only seems to contain 450 MB and using filesystem Extended 3 (all this according to System/Administration/Disks).

I also seem to have a another hard drive listed containing Partition Ntu-Root and some kind of Swap-file, but this is maybe normal?

My questions is: Can I in some way make one partition of my 20 GB disk and run everything from there without reinstalling Ubuntu? If I have to reinstall, what should I choose in the Partition manager to get everything working (didn't get any suitable options as far as I could see).

If this is too much trouble, can I in some way format the existing Partition 5 and get it to work as a disk drive?

I'm totally new to this and don't know much about Linux commands etc. but would really like to learn more.

---

### Post by John.Michael.Kane on 2006-02-03
you can try using gparted. if this is not a viable option. you can reinstall ubuntu.
setting up your partions like so.
1g for swap and everthing else for your install. if you want to get fancy you can split it in threes ie: 2gig for boot and root 1gig for swap the rest for your home file..

---

### Post by erj80 on 2006-02-03
OK, tried Gpart but didn't understand how to get it working, tried to convert to ext3 filesystem but program said it couldn't change a mounted device so maybe my 18,43 GB are mounted and existing in some way?

Otherwise I will try and reinstall, my problem is I don't understand how to sort out the partitioning process and all the different options.

---

### Post by Greg2 on 2006-02-03
[QUOTE=erj80] Otherwise I will try and reinstall, my problem is I don't understand how to sort out the partitioning process and all the different options.[/QUOTE]
I would suggest (if you haven’t set up too many things yet that require a lot of time) to just reinstalling the system. I would recommend making 3 primary partitions with the installer like this:

hda1 as /  formatted with ext3 (this is for your file system with root ownership) Note: I world suggest making this at least 4 GB or more if you plan (and you will if you keep using Linux) on compiling you’re own kernels?

hda2 as /swap  formatted with linux swap (this should be ‘at least’ 1.5x your memory in MBs) Note: IMHO swap works more efficiently in the middle of the drive... some users here may disagree.

hda3 as /home  formatted with ext3 (this is for your personal files and documents so you do not need to use sudo to work on them) Note: I would use the rest of the drive space for this.

Please note that this is ‘just my personal opinion’ of how to set up your laptop with one Linux OS... it does however work very well for me. :)

---

### Post by Herman on 2006-02-03
> Otherwise I will try and reinstall, my problem is I don't understand how to sort out the partitioning process and all the different options.If you do decide to re-install, just have a look [here]("http://users.bigpond.net.au/hermanzone/p2.htm"), it's really for dual booting, more info than you really need to know, only some of it applies to you. Some of it you can ignore. Some of it might help.
If you are looking at it, when you get to the step in illustration 8, choose 'Erase entire disk'. The next few steps are about dual booting, but since you aren't doing that, you can skip those, as the option to 'Erase entire disk' will apportion your main ext3 operating system partition (/), and your swap area automatically for you. Some of the rest of it from step 11 down will apply to you, but you can probably skip the part about GRUB to. That will likely be done automatically for you too. That's the simplest way.
> hda1 as / formatted with ext3 (this is for your file system with root ownership) Note: I world suggest making this at least 4 GB or more if you plan (and you will if you keep using Linux) on compiling you’re own kernels?
hda2 as /swap formatted with linux swap (this should be ‘at least’ 1.5x your memory in MBs) Note: IMHO swap works more efficiently in the middle of the drive... some users here may disagree.
hda3 as /home formatted with ext3 (this is for your personal files and documents so you do not need to use sudo to work on them) Note: I would use the rest of the drive space for this. The set-up above by Greg2 would be alright too, it's up to you. If you want an idea how to use the partitioner for that, see [this]("http://users.bigpond.net.au/hermanzone/p14.htm") one. Once again, it is for dual booting, you can ignore some of it, but you might get some ideas from it that might help you understand how to use the partitioner.
 :-D (Herman)

---

### Post by Greg2 on 2006-02-03
[QUOTE=Herman].If you do decide to re-install, just have a look [here]("http://users.bigpond.net.au/hermanzone/p2.htm"), it's really for dual booting, more info than you really need to know, only some of it applies to you. Some of it you can ignore. Some of it might help.[/QUOTE]
I like the way you’ve made that with the actual pics of the installer. Good job!

If you don’t mind I will give these links to the new users that I find having problems with this?

---

### Post by Herman on 2006-02-03
>  If you don’t mind I will give these links to the new users that I find having problems with this?Sure, Greg2, certianly, that's what it's for, and if more new users have it then I hope they will have less trouble and like Ubuntu better as a result. A few others also give it out, the more the better! I'm glad if people like it. Thanks! :D (Herman).

---

