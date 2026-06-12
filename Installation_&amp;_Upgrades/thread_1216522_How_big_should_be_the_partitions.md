---
title: "How big should be the partitions?"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-07-18
I am planning on installing version 9.04.

I'd like to put each of the following in separate partitions:
/boot
/home
/opt
swap

This would facilitate using more than 1 version of Ubuntu, even more than 1 Linux distro.

Windows will still be my main production system, but there are *ix tools, such as Bluefish, that I wish to use, and I wish to install XAMPP for Linux. I already have XAMPP Lite for Windows.

A bit over 2 years ago, I installed version 7.04 in a 32GB partition, with a 2G partition for the swap. Since I cannot easily upgrade 7.04, I have deleted it, and will install 9.04.

I definitely wish to separate /boot, /home, and /opt.
I've seen a recommendation of 20GB for each of /boot and /home, and 5GB for swap. Did not address /opt.

What are the recommended sizes for each of the 4 partitions?

---

### Post by ptn107 on 2009-07-18
/boot
-Ubuntu as default sets it to 255mb when it is separated from / (my /boot only uses 14.3mb on my system right now with multiple kernels installed) so 255mb is fine if not too much.  20gb is certainly overkill.

/home
-whatever is left over, since this is where all your personal stuff goes

/opt
-never really used it since Ubuntu puts software in the folders where they need to go.  Personally I would not separate this folder from / unless you have a bunch of home-grown software you manually install.

/swap
-up to 2gb but not exceeding, anything more is just a waste and indicates you don't have enough actual RAM.  5gb is way way too much.

/
-The most I ever allocated to root is 12gb (as I am not running a server).  I have never come close to the max (currently / is using only 4gb of the 12 and I have tons of software installed on this machine).  Games however may take up a lot of space if you install many.

---

### Post by raymondh on 2009-07-18
> **ptn107 said:**
> /boot
-ubuntu as default sets it to 255mb when it is separated from / (my /boot only uses 14.3mb on my system right now with multiple kernels installed) so 255mb is fine if not too much.  20gb is certainly overkill.

/home
-whatever is left over, since this is where all your personal stuff goes

/opt
-never really used it since ubuntu puts software in the folders where they need to go.  Personally i would not separate this folder from / unless you have a bunch of home-grown software you manually install.

/swap
-up to 2gb but not exceeding, anything more is just a waste and indicates you don't have enough actual ram.  5gb is way way too much.

/
-the most i ever allocated to root is 12gb.  I have never come close to the max (currently / is using only 4gb of the 12 and i have tons of software installed on this machine).  Games however may take up a lot of space if you install many.

+1.

---

### Post by darco on 2009-07-18
> **ptn107 said:**
> /boot
-Ubuntu as default sets it to 255mb when it is separated from / (my /boot only uses 14.3mb on my system right now with multiple kernels installed) so 255mb is fine if not too much.  20gb is certainly overkill.

/home
-whatever is left over, since this is where all your personal stuff goes

/opt
-never really used it since Ubuntu puts software in the folders where they need to go.  Personally I would not separate this folder from / unless you have a bunch of home-grown software you manually install.

/swap
-up to 2gb but not exceeding, anything more is just a waste and indicates you don't have enough actual RAM.  5gb is way way too much.

/
-The most I ever allocated to root is 12gb (as I am not running a server).  I have never come close to the max (currently / is using only 4gb of the 12 and I have tons of software installed on this machine).  Games however may take up a lot of space if you install many.

+1
Dont waste space on the / partition, mine is 10gb and barely am using half of it...

I have 8gigs of ram, my swap is _256mb_.....

No OPT tho...

this is the best way to setup your partitions, which makes it alot easier to upgrade your since OS in the future...

darco

---

### Post by Howard Kaikow on 2009-07-18
Thanx, see my comments below.

> **ptn107 said:**
> /boot
-Ubuntu as default sets it to 255mb when it is separated from / (my /boot only uses 14.3mb on my system right now with multiple kernels installed) so 255mb is fine if not too much.  20gb is certainly overkill.

Ah, then I am asking the wrong question.

I also need to separate / root (see below).

> **ptn107 said:**
> /home
-whatever is left over, since this is where all your personal stuff goes

Left over from what?

Drive is 72GB.

8GB is taken by an NTFS partition used by Windows, but that partitition will eventually grow. So all the ubuntu stuff should be located prior to the NTFS partition to faciliate growth of the NTFS partition.

Due to tight space on other drives, I should put the swap partition on the same drive as Ubuntu. So that would be 2GB.
But the system has only 768MB of memory (it's an 11 year old critter), should I increase the size of the swap partition?

> **ptn107 said:**
> /opt
-never really used it since Ubuntu puts software in the folders where they need to go.  Personally I would not separate this folder from / unless you have a bunch of home-grown software you manually install.

Never thought about /opt until today.
XAMPP for Linux wants to be installed in /opt.

Indeed the 8GB NTFS partition on the drive was created to install XAMPP Lite in Windows, and I put a bunch of other stuff in the partition to save space on other drives.

Unless I use XAMPP's Alias to refer to files, all files have to be under /opt. for example in Windows, they all have to be under S:\xampplite\htdocs\xampp.

I would keep a copy of my web site under that directory, so I have just XAMPP, and my files, in /opt. Of course, I do not yet know how much space XAMPP itself takes. In Windows XAMPP + my files currently takes about 166MB. I expect that 2GB should be more than enough. 

/swap
-up to 2gb but not exceeding, anything more is just a waste and indicates you don't have enough actual RAM.  5gb is way way too much.[/QUOTE]

Is 2GB enough with only 768MB of memory?

> **ptn107 said:**
> /
-The most I ever allocated to root is 12gb.  I have never come close to the max (currently / is using only 4gb of the 12 and I have tons of software installed on this machine).  Games however may take up a lot of space if you install many.

I do not install games, movies, etc.

How are / and /boot related in terms of using more than one version of Ubuntu, or different versions of Linux?

Would not I need a different / for each?
In which case, I might as well leave /boot in /.

What about the following?

16GB for /
If needed, a small partition for /boot.
8GB for /home
2GB, or more, for swap.
4GB for /opt, likely shrinking as I learn more.

---

### Post by Howard Kaikow on 2009-07-18
> **ptn107 said:**
> /boot
-Ubuntu as default sets it to 255mb when it is separated from /


 I forgot to ask.

What does it man tat Ubuntu is separated from /?

Ubuntu gets installed in a partition, I though that was /??
So there is a separate / partition?
How does one set that up?
Alas, last night I deleted 7.04, so I cannot see what I did.

So, I'm now taking about the following partitions:

/
/home
/opt
swap
Maybe, /boot

---

