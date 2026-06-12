---
title: "Disk full - Stuck"
date: 2008-11-27
forum: General Help
---

### Post by dznn on 2008-11-27
Hi,

I have Eeepc 901 with Ubuntu 8.10 and a big problem...

I has two small ssd disks ( total 12gb, I think its one of 7.5gig and one of 4.5 gig ) Now when I installed the system I wasn't really thinking.. forgot you don't really get to choose where applications are installed... And I assigned the '/' to the 4.5 one and my /home to the 7.5 one.

Now... My small one is full... No problem I thought I'd just remove some app's..But I can't! Can't even open synaptic or the normal install/remove app ( the later I can open but can't use ) because my disk is full... I tried 'dpkg --configure -a' but even that one can't finish because my disk is full. I tried 'apt-get clean' but that doesn't help neihter..

I think the problem is somewhere dpkg keeps a cache of programs it downloaded but haven't got the room or time to finish download and I need to remove that part so I have some room to delete aps. Why I suspect this? Well I was installing 'Kile' when it happend but it never got installed ( its a large app +- 380mb I think ).

So, can someone tell me if this is the case and how I should fix it.
Second: Is it possible to shrink my 'large' partition and add a part of it to the root ( '/' )? Otherwise I can't install anymore applications...

Or are there other solutions?

Thx in advance.

---

### Post by kpkeerthi on 2008-11-27
From GRUB menu, Choose 'Recovery Mode'. And at the command prompt run this command:
```
sudo apt-get clean
```
to clean the cached debs.

You may use gparted that comes with Ubuntu Live CD to resize your partitions. Its available under System -> Admin -> Partition Editor. Or google gparted live cd.

---

### Post by dznn on 2008-11-27
Thanks for your fast answer but... I already tried sudo apt-get clean.. Does it make a difference when i'm in recovery mode?

And I know u can use gParted to resize them but can I accolate empty space on another disk to an already existing filesystem's '/' ?

---

### Post by kpkeerthi on 2008-11-27
> Thanks for your fast answer but... I already tried sudo apt-get clean.. Does it make a difference when i'm in recovery mode?
Try it. That what it is for - the recovery mode.

---

### Post by dznn on 2008-11-27
Hi,

I booted in recovery mode ( tried the 'clean' menuoption first but that didn't really do something ) then I chose the 'resume normal boot' option and tried "sudo apt-get clean" in the shell.

Now I can start synaptic and remove programms. Thx!!

Any Idea on my other question?

---

### Post by Ric_ on 2008-11-27
Hey man try going to /var/log

and remove all the .gz files. This should clear lots of space up. You'll need to use sudo for this.

Also have you tweaked ubuntu the eePC way to stop lots of the loging and writing to disk?

You might want to look into that especially if you have a SSD harddisk.

---

### Post by kpkeerthi on 2008-11-27
I guess it might be something else that is taking up your space and not the cached deb files.

---

### Post by kpkeerthi on 2008-11-27
How many kernels do you have installed?

Uninstall the ones you don't need (from recovery mode).
[http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/](http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/)

---

### Post by dznn on 2008-11-27
Hmmz.. I tought it was solved but I isn't... 
I got into synaptic and tried removing evolution and OpenOffice ( two huge applications ) but before it ended I got the error again recommending me to use "dpkg --configure -a" but dpkg can't finish that... I always get the error:
```

dpkg: ../../src/packages.c:221: process-queue: Assertion 'dependtry <= 4' failed
.
Aborted

```

Anyone knows what this means?

I removed the .gz files like you said and I makes a HUGE difference! Thx alot for the hint? What did you mean with the tweaks for eeePc? I use adam's kernel that's my only real tweak.

I used Disk Usage Analyser and noticed my /usr dir is 2gb.. howcome? Can I move that to other disk?

And does sombody know the answer to my previous question:
> 
And I know u can use gParted to resize them but can I accolate empty space on another disk to an already existing filesystem's '/' ?


I'm really grateful for all the fast help!

---

### Post by kpkeerthi on 2008-11-27
With gparted you can shrink a partition and add the free space thus produced to an existing partition. 

I have done that and it is reliable 99.99% of the time. Always backup your data before you mess with your partitions.

---

### Post by dznn on 2008-11-27
Hehe, there is no place to backup :) Haven't got one of those nifty extern hdd's :) And I tried to remove previous kernels but there is just one ( 2.6.27-7.16 ) and I'd like to keep that one for when my eeepc-kernel fails.

---

### Post by CatKiller on 2008-11-27
> **DeathZan said:**
> Second: Is it possible to shrink my 'large' partition and add a part of it to the root ( '/' )? Otherwise I can't install anymore applications...

Not as such. You can only have one /. You could probably use some Logical Volume Manager method, but I have no idea how that works.

However, you could make a new partition on your larger drive and mount it at /usr, or some other useful part of your filesystem tree. Which part would be most useful for you to move depends on your usage patterns. You might find that /usr would provide the most benefit, or it might be /var.

Obviously you'll need to copy the contents of your old /usr to your new partition, else things will stop working. If you have some kind of live environment available, it would probably be easiest to do the operation using that, since otherwise at some point you'd have to stop using your old /usr and start using the new one. Complicated.

A slightly less traditional approach could have you just moving directories to your larger drive and using links on the small drive to point to the real files. Not very tidy, though.

---

