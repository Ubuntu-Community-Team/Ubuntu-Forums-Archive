---
title: "Installing HighPoint Rocketraid 454"
date: 2008-05-01
forum: Hardware
---

### Post by mballow223 on 2008-05-01
I am trying to install the HighPoint RocketRaid 454, and I am following this turorial:  [http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6)          however i am getting this error:
root@Ubuntu-x64:/home/mballow223# cd /home/mballow223/RocketRaid/hpt374
root@Ubuntu-x64:/home/mballow223/RocketRaid/hpt374# make
cp -f raid-x86_64.o raid.obj
make -C /usr/src/linux-headers-2.6.24-16 SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-16/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/mballow223/RocketRaid/hpt374/hpt.o
/home/mballow223/RocketRaid/hpt374/hpt.c:1:26: error: linux/config.h: No such file or directory
In file included from /home/mballow223/RocketRaid/hpt374/hpt.c:161:
/home/mballow223/RocketRaid/hpt374/entry.c:88: error: ‘MUTEX_LOCKED’ undeclared here (not in a function)
/home/mballow223/RocketRaid/hpt374/entry.c: In function ‘scsicmd_buf_get’:
/home/mballow223/RocketRaid/hpt374/entry.c:271: error: ‘struct scatterlist’ has no member named ‘page’
/home/mballow223/RocketRaid/hpt374/entry.c:271: error: ‘OS_KMAP_TYPE’ undeclared (first use in this function)
/home/mballow223/RocketRaid/hpt374/entry.c:271: error: (Each undeclared identifier is reported only once
/home/mballow223/RocketRaid/hpt374/entry.c:271: error: for each function it appears in.)
/home/mballow223/RocketRaid/hpt374/entry.c: In function ‘hpt3xx_Detect’:
/home/mballow223/RocketRaid/hpt374/entry.c:767: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/mballow223/RocketRaid/hpt374/entry.c:767: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/mballow223/RocketRaid/hpt374/entry.c:768: error: ‘SA_INTERRUPT’ undeclared (first use in this function)
/home/mballow223/RocketRaid/hpt374/entry.c:768: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/mballow223/RocketRaid/hpt374/entry.c: In function ‘hpt3xx_Reset’:
/home/mballow223/RocketRaid/hpt374/entry.c:837: error: ‘Scsi_Cmnd’ has no member named ‘pid’
/home/mballow223/RocketRaid/hpt374/entry.c: In function ‘fOsBuildSgl’:
/home/mballow223/RocketRaid/hpt374/entry.c:1028: error: ‘struct scatterlist’ has no member named ‘page’
/home/mballow223/RocketRaid/hpt374/entry.c: In function ‘hpt_worker_thread’:
/home/mballow223/RocketRaid/hpt374/entry.c:1226: warning: unused variable ‘sem’
make[2]: *** [/home/mballow223/RocketRaid/hpt374/hpt.o] Error 1
make[1]: *** [_module_/home/mballow223/RocketRaid/hpt374] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16'
make: *** [default] Error 2


Thanks for your help.

---

### Post by davidgloriam on 2008-05-03
I managed to get my Highpoint Rocketraid 1520 working by following the advice on [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by tachyon47 on 2008-05-15
I had a similar problem to the OP. I'm still looking for a solution. I dunno about that link on the wiki, that seems to be instructions for setting up software RAID. I know the 454 card kinda sucks, but I'm pretty sure it is a real hardware RAID controller.

Anyone know how to get that stupid driver to build?

---

### Post by whatever69 on 2008-05-15
At the moment, your driver won't build with the 2.6.24 kernel.  A few structs and header files have changed.  Highpoint needs to update their driver.

For example:

- struct semaphore *tn;
+ struct completion *tn;

- up(&tn);
+ complete(&tn);

- down(&tn);
+ wait_for_completion(&tn); 

- DECLARE_MUTEX_LOCKED(tn);
+ DECLARE_COMPLETION(tn); 

- SA_INTERRUPT 
+ IRQF_DISABLED

- SA_SHIRQ
+ IRQF_SHARED

just to name a few.  you can change them in the entry.c, but it's a pain.  If you have free time...

---

### Post by tachyon47 on 2008-05-16
> **whatever69 said:**
> At the moment, your driver won't build with the 2.6.24 kernel.  A few structs and header files have changed.  Highpoint needs to update their driver.

For example:

- struct semaphore *tn;
+ struct completion *tn;

- up(&tn);
+ complete(&tn);

- down(&tn);
+ wait_for_completion(&tn); 

- DECLARE_MUTEX_LOCKED(tn);
+ DECLARE_COMPLETION(tn); 

- SA_INTERRUPT 
+ IRQF_DISABLED

- SA_SHIRQ
+ IRQF_SHARED

just to name a few.  you can change them in the entry.c, but it's a pain.  If you have free time...

AHH now that explains a lot. Ok, thanks for the info. I wonder if I'd get anywhere by complaining to highpoint or if i'm just SOL for now

Thanks again,
-T

---

### Post by whatever69 on 2008-05-17
I would kindly remind them ;)  Copy paste some of these changes.  I'm sure their developers will enjoy the little cheat sheet.

---

### Post by s0rken on 2008-06-03
Don't know if this is of any help for you, but I managed to compile the driver successfully in Gutsy (following stefan freyers howto). The difference was that I replaced **linux.h** with **autoconf.h** in **hpt.c**, and switched from the **2.6.22-14-server** kernel to **2.6.22-14-386** in Gutsy. Was hoping to upgrade to Hoary soon, so if you manage to solve it I'd be happy to know :)

---

### Post by Lutiana on 2008-06-08
> **whatever69 said:**
> At the moment, your driver won't build with the 2.6.24 kernel.  A few structs and header files have changed.  Highpoint needs to update their driver.

For example:

- struct semaphore *tn;
+ struct completion *tn;

- up(&tn);
+ complete(&tn);

- down(&tn);
+ wait_for_completion(&tn); 

- DECLARE_MUTEX_LOCKED(tn);
+ DECLARE_COMPLETION(tn); 

- SA_INTERRUPT 
+ IRQF_DISABLED

- SA_SHIRQ
+ IRQF_SHARED

just to name a few.  you can change them in the entry.c, but it's a pain.  If you have free time...

Can you name the rest so I can make the changes? I will then make the entry.c file available (and the compiled modules). I don't have the time, but I really need to get this card working and if that means manula entry then so be it.... :(

Thanks

---

### Post by whatever69 on 2008-06-09
> **Lutiana said:**
> Can you name the rest so I can make the changes? I will then make the entry.c file available (and the compiled modules). I don't have the time, but I really need to get this card working and if that means manula entry then so be it.... :(

Thanks

Sorry :( but naming the rest doesn't automatically mean it'll work.  It just means it may compile.  Either way, this is only if you want the proprietary driver from highpoint.  Your card should've been picked up automatically by the Linux Kernel.  please note that I have the 1640 card and my experience is only with that card.

---

### Post by Lutiana on 2008-06-10
Okay, so I emailed Highpoint and got this response:

> 
from	Support <support@highpoint-tech.com>
to	******************
date	Tue, Jun 10, 2008 at 10:16 AM
subject	Re: RocketRAID 454 (HPT374) Driver support
	
Hello,

Updates are still planned, but a release date has not been set.

Regards,

HighPoint Technologies, Inc.
Customer Support Department

[http://www.highpoint-tech.com](http://www.highpoint-tech.com)
[http://www.hptmac.com](http://www.hptmac.com)



So I have switched to a software Raid 5. I had to disable the raid in the RR454 bios for it to work properly and then I followed this tutorial:

```

http://mywheel.net/blog/index.php/software-raid-in-ubuntu/

```

Only thing to note is his english is not very good and can be a little confusing, and when he tells you to use the cylinder size I recommend using the actually Byte size, since different manafacturers will have different cylinder counts to achieve the total size (should be typed in as +xxxxxxxK in fdisk).
 
He also uses reiserfs, but from what I gather this is not a good choice for ubuntu, but I have not played with this part too much yet.

He also does not tell you how to add the new raid to etc/fstab, but this site was very good to work out how to add it:

```

http://www.tuxfiles.org/linuxhelp/fstab.html

```

And lastly, once you have it all setup you check the partition and file system to make sure it is the right amount of space using the fs command (i have not tried it yet):

```

http://www.computerhope.com/unix/udf.htm

```

And lastly here is a page for more information on msadm
```

http://www.linuxmanpages.com/man8/mdadm.8.php

```

Hope this helps!

---

### Post by Reyudo on 2008-06-19
whatever69 I don't know how to thank you your usefull (to me) respond, and i have registered only to post it. Thanks (i have examn on monday about something similar and all i have founded was useless, i was coming crazy!). Thanks again (excuse me my english, i am a typical spanish!).

 Jejeje, Now I know where is the fuc*** buttom of thanks!

---

### Post by Dafoe on 2008-07-22
> **s0rken said:**
> Don't know if this is of any help for you, but I managed to compile the driver successfully in Gutsy (following stefan freyers howto). The difference was that I replaced **linux.h** with **autoconf.h** in **hpt.c**, and switched from the **2.6.22-14-server** kernel to **2.6.22-14-386** in Gutsy. Was hoping to upgrade to Hoary soon, so if you manage to solve it I'd be happy to know :)

So you managed to compile the driver but did you get everything else to work ?

I tried compiling the driver for kernel 2.6.24-19-386 and symlinking autoconf.h to config.h in /usr/src/linux/include/linux/ where /usr/src/linux is symlinked to /usr/src/linux-headers/2.6.24-19-386 but that did not work.

---

### Post by Dafoe on 2008-07-23
I got Rocketraid 454 to work just now and for the record I've been following Stefans excellent guide on this matter: [http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6)

So first things first, I was getting the same make error where it complained about config.h being missing when using kernel 2.6.24-19-server and I went ahead and tried a few different kernels, though all of them Hardy Heron (8.04) and none of them worked. 

I then fetched Dapper Drake (6.06, server to be supported to 2011), installed it, followed the guide step by step and it worked! (there was one obvious step missing though: apt-get install make gcc)

If you're like me, running a home server on an old PC you probably won't mind running a older version of ubuntu, the main issue is to get the raid to work because that's likely the only function of the old server. 

Hope this helps someone.

---

### Post by Dafoe on 2008-07-23
> **Dafoe said:**
> I got Rocketraid 454 to work just now and for the record I've been following Stefans excellent guide on this matter: [http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6)

So first things first, I was getting the same make error where it complained about config.h being missing when using kernel 2.6.24-19-server and I went ahead and tried a few different kernels, though all of them Hardy Heron (8.04) and none of them worked. 

I then fetched Dapper Drake (6.06, server to be supported to 2011), installed it, followed the guide step by step and it worked! (there was one obvious step missing though: apt-get install make gcc)

If you're like me, running a home server on an old PC you probably won't mind running a older version of ubuntu, the main issue is to get the raid to work because that's likely the only function of the old server. 

Hope this helps someone.


Oobs, forgot to mention that I got this working on kernel: 2.6.15-51-server

over and out

---

### Post by whatever69 on 2009-01-16
> **Lutiana said:**
> Okay, so I emailed Highpoint and got this response:

from Support <support@highpoint-tech.com>
to ******************
date Tue, Jun 10, 2008 at 10:16 AM
subject Re: RocketRAID 454 (HPT374) Driver support

Hello,

Updates are still planned, but a release date has not been set.

Regards,

HighPoint Technologies, Inc.
Customer Support Department

[http://www.highpoint-tech.com](http://www.highpoint-tech.com)
[http://www.hptmac.com](http://www.hptmac.com)


You go that response in June.  Shortly after in July, a driver with the fixes we wanted was released:

    v2.19 07/10/2008
           Fix compile error on 2.6.25.
           Pass all PIO IDE Pass through command to device.
           Support ATA DMA command(0xc8/0xca) in IDE_PASS_THROUGH_IOCTL.


I just compiled the driver with no problems whatsoever on Ubuntu 8.10 2.6.27-9-generic kernel:
```

$tar xvzf hpt374-src-v2.19-080710.tgz
$sudo make KERNELDIR=/usr/src/linux-headers-2.6.27-9-generic/
```

or in my case, I don't want RAID since I just use the card as a SATA controller with the disk in JBOD mode:

```
$sudo make KERNELDIR=/usr/src/linux-headers-2.6.27-9-generic/ NON_RAID=1
```

Yeah.  It's been many months.

To install, I followed these instructions:  [http://ubuntuforums.org/showthread.php?t=543872](http://ubuntuforums.org/showthread.php?t=543872)

---

### Post by whitechinaman on 2009-10-03
I realize that this post has been inactive for a while, but I am unable to get my Highpoint card to work in my new Kubuntu installation. I'm running 9.04, and just ran all updates. I have been running Debian for the last several years, and the card worked fine using the instructions from this site: [http://lukav.com/wordpress/2008/02/22/howto-install-hpt374-raid-driver-in-debian](http://lukav.com/wordpress/2008/02/22/howto-install-hpt374-raid-driver-in-debian). But under Kubuntu, there are varying how to's on this site describing how to make it work, and it seems only some people are actually successfully setting it up. I'm not interested in a software raid, because I've had to do a full reinstall several times and having my info on a hardware raid makes it easy to just re-access my existing raid setup (raid 5 with 3 drives) after an OS drive fails (which has happened twice). 

Anyhow, I've followed the abovementioned advice on seting this up, along with the instructions for making it work in Debian, but I keep getting the following error messages:

root@jason-desktop:/usr/src/hpt374# make KERNELDIR=/usr/src/linux-headers-2.6.28-15-generic ARCH=x86_64
cp -f raid-x86_64.o raid.obj
make -C /usr/src/linux-headers-2.6.28-15-generic SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /usr/src/hpt374/hpt.o
/usr/src/hpt374/hpt.c: In function ‘get_bdev’:
/usr/src/hpt374/hpt.c:114: error: too many arguments to function ‘blkdev_get’
/usr/src/hpt374/hpt.c:118: error: too few arguments to function ‘blkdev_put’
/usr/src/hpt374/hpt.c: In function ‘sd_inuse’:
/usr/src/hpt374/hpt.c:131: error: too few arguments to function ‘blkdev_put’
In file included from /usr/src/hpt374/hpt.c:165:
/usr/src/hpt374/hptproc.c: In function ‘get_sd_name’:
/usr/src/hpt374/hptproc.c:505: error: too few arguments to function ‘blkdev_put’
make[2]: *** [/usr/src/hpt374/hpt.o] Error 1
make[1]: *** [_module_/usr/src/hpt374] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2

If anyone can help me make this work, that would be great. I love Kubuntu so far, but if I cant make this work I will have to go back to Debian :(  I've just got too much data on that raid that I can't afford to lose (over 400GB of pics, music, financial info, etc.)

---

### Post by ethersphere on 2010-01-01
what did you end up doing in the end?

I'm currently downloading ubuntu 8.10 to see if that would work.

---

### Post by whitechinaman on 2010-01-10
Well, I'm not proud about what I had to do, but it was my only option. I use debian for my desktop, and I've set up a second computer as a file server running XP. The drivers I had been using previously under debian no longer work either. And this is going to have to be my "duct tape" solution until I can afford to buy another raid card that plays better with Linux. Its kind of frustrating actually, I only bought this card a couple years back, and paid over $100USD too. Oh well, no OS is perfect.

---

### Post by ethersphere on 2010-01-11
Oh man, back to XP.  Well, I tried installing ubuntu 8.X with no luck.
So what I did is install FreeNAS (freenas.org) and it supports the raid card right out of the box.  I also have it set up as a UPNP server for PS3, XBOX, and the like.  It supports file sharing for Windows, Linux, and even MAC.  I also enabled remote torrent downloading (you save a torrent file to a folder it monitors and it starts downloading!).FreeNAS is based on FreeBSD, not linux though very similar, but there's plenty of information on the site and the web interface is really easy to use (seemed easier than installing ubuntu server).

Hope this helps, can't think of a reason to try ubuntu again unless you really want to use the raid card on your desktop as opposed to a server rig.

---

### Post by whitechinaman on 2010-01-11
Thanks, ethersphere, I will definitely check out FreeNAS.  I've been looking for an excuse to try some flavor of Unix. And no, I have no particular need or desire to use ubuntu persay, I just liked how easily it installed on my laptop so I figured I'd try it on my desktop as well. I'm actually more of a Debian guy.

---

