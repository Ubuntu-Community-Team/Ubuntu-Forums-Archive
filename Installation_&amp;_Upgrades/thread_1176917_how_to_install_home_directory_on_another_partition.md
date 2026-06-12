---
title: "how to install /home directory on another partition?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by xsk3l3t0rx on 2009-06-02
hello all. ive decided that i am just going to use one 1TB hdd for my linux installation, i want to separate my /home directory from the system directories, this way if i screw up something in ubuntu, i can just reinstall the system. also, if i am installing 2GB of ram, do i really need a swap? how would you folks go about this? i tend to do stupid things and mess up my ubuntu system partitions while trying to fiddle with linux, and id really not like to lose all my multimedia in the process. thank you for all your help ppl.

---

### Post by raymondh on 2009-06-02
> **xsk3l3t0rx said:**
> hello all. ive decided that i am just going to use one 1TB hdd for my linux installation, i want to separate my /home directory from the system directories, this way if i screw up something in ubuntu, i can just reinstall the system. also, if i am installing 2GB of ram, do i really need a swap? how would you folks go about this? i tend to do stupid things and mess up my ubuntu system partitions while trying to fiddle with linux, and id really not like to lose all my multimedia in the process. thank you for all your help ppl.

Hi,

Have a look-see at psychocats guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As for SWAP .... it'll be invaluable if you use suspend a lot.

Good luck and regards,

---

### Post by albinootje on 2009-06-02
> **xsk3l3t0rx said:**
> i want to separate my /home directory from the system directories, this way if i screw up something in ubuntu, i can just reinstall the system. 

Good idea :)

This might be useful : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

> 
also, if i am installing 2GB of ram, do i really need a swap?

Well, this is a difficult question to answer. Swap is always good, esp. when you have loads of diskspace anyway, but.. the ancient rule of thumb "use twice as much as the amount of RAM you have" might be too much in your case.

---

### Post by Hello71 on 2009-06-02
> **albinootje said:**
> Good idea :)

This might be useful : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)



Well, this is a difficult question to answer. Swap is always good, esp. when you have loads of diskspace anyway, **but.. the ancient rule of thumb "use twice as much as the amount of RAM you have" might be too much in your case.**

That's not an ancient rule of thumb according to this guy from MS...

[http://blogs.technet.com/markrussinovich/archive/2008/11/17/3155406.aspx](http://blogs.technet.com/markrussinovich/archive/2008/11/17/3155406.aspx)

---

### Post by presence1960 on 2009-06-02
If you haven't installed Ubuntu yet you can partition your disk prior to install with the Ubuntu Live Cd or gparted Live CD. Once you have your partitions set up you can install. At the partitioner screen Prepare disk space choose manual option. Click forward. this will bring up your disk(s) & partitions. Highlight the one you want as root. Click Edit partition. choose filesystem and set mountpoint to " / ". Click Ok. Then highlight the partition you want to use as /home. Click Edit partition. Set filesystem type and set mountpoint to " /home ". If you already have data on this /home **_make sure format box is unticked_** or you will lose your data. Highlight partition you want for swap and instead of a filesystem select swap. Proceed with the install.

If you already have Ubuntu installed try the link provided in the previous posts from pychcats.

---

