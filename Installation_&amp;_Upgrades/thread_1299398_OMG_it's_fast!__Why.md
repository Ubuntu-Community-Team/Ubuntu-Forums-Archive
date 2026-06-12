---
title: "OMG it's fast!  Why?"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-10-23
WTF!  How was this done?????

I'm on a Pentium 3, 800 MHz with 256 MB of RAM . . . O.K.?

'Just installed the release candidate of Xubuntu 9.10.

Time from pressing the power-on button to seeing my desktop is less than one minute!!!!!

O.K., I'm not connected to the internet, but still.  What's going on here?  Why the lightning speed????

Responsiveness is also great but I haven't installed Nvidea drivers yet so some apps are too heavy on memory usage.

Wow!!!

I'm reserving judgment until I get all my software and drivers installed and I have an internet connection, but wow!

Cheers!!

> 9.10 has more aggressive use of upstart than 9.04 did, so you may be getting better parallism and fewer unnecessary timeout delays during the boot process. Also, 9.10 defaults to ext4 filesystem; if you were comparing it to 9.04 on ext3 that may also have made a difference.

Thanks Lemming465, that's some information I didn't know about.  Yes, I was comparing to 9.04 with ext3 as it was default when I installed 9.04.

---

### Post by stinger30au on 2009-10-23
no antivirus, anti spam, anti trojan, anti malware, crud to eat up cpu cycles


this is one reason, theres plenty more

---

### Post by doomsword2001 on 2009-10-23
xubuntu has a light interface :D i used to have it on a pentium 3 aswell

---

### Post by Nopposan on 2009-10-24
No, guys.  You don't get it.  This is a slow machine.  I've tried Xubuntu on machines like this before and the boot time has been in the 3-4 minutes range.

Check out this link:
[http://arstechnica.com/open-source/reviews/2009/09/ubuntu-910-alpha-6-released-boot-optimizations-arrive.ars]("Ubuntu 9.10 is fast!")

Also. [https://wiki.ubuntu.com/FoundationsTeam/BootPerformance]("https://wiki.ubuntu.com/FoundationsTeam/BootPerformance")

'Something about prefetching.

Cheers.

---

### Post by Rocket2DMn on 2009-10-24
One of the goals of the Jaunty release was to speed up boot times, and they did an excellent job at it :)

---

### Post by Steveway on 2009-10-24
> **Rocket2DMn said:**
> One of the goals of the Jaunty release was to speed up boot times, and they did an excellent job at it :)

Not really. Using Ubuntu my start-up time went down by more than 20 seconds compared to the same setup using Debian.
On Debian I got a start-up Time of 36 seconds on an 1GHZ P3 with 256MB of RAM but Ubuntu 9.10 suffers at a measily 59 seconds.
The problem is that I got 39 seconds on Ubuntu 9.10 at Alpha 1 so this is a serious let-down. :-/

---

### Post by SuperSonic4 on 2009-10-24
So you can get on in a few seconds but that's next to useless in the great scheme of things

---

### Post by Nopposan on 2009-10-24
In the GRAND scheme of things, what exactly is useful and to whom?

Well, let's not get too theological, eh?

I think making a ten year old computer boot three or four times faster now than it ever has is pretty darn cool; also, it will go over great with those who are trying to decide whether or not to switch to a new operating system.

BTW, I tried Jaunty on a machine like this too and it was nothing like this fast.  Karmic is really something in a class by itself when it comes to boot speed.

---

### Post by winotree on 2009-10-24
> I think making a ten year old computer boot three or four times faster now than it ever has is pretty darn cool; also, it will go over great with those who are trying to decide whether or not to switch to a new operating system.

That was very well said.

---

### Post by SuperSonic4 on 2009-10-25
I feel so liberated with boot time - just think of all the things I can do with an extra 40 second

---

### Post by lemming465 on 2009-10-25
9.10 has more aggressive use of upstart than 9.04 did, so you may be getting better parallism and fewer unnecessary timeout delays during the boot process.  Also, 9.10 defaults to ext4 filesystem; if you were comparing it to 9.04 on ext3 that may also have made a difference.

---

### Post by GGreen on 2009-10-27
I agree on the speed.  The desktop that I installed on has 256 ram and 40 gig hard drive.  The computer is 5 or 6 years old and was sloooooow with XP.  It is surprising how fast it is online too.

My only beef is that XP was completely wiped out on install and it won't boot unless I use Super Grub Disk for Grub2.

I've upgraded my laptop from Vista to Ubuntu, my dad's desktop from XP to Ubuntu and a friend's brand new laptop from Vista to Ubuntu.  My wife is next...if I can ever get her off the computer.

---

### Post by CardPlay3r on 2009-10-27
> **stinger30au said:**
> no antivirus, anti spam, anti trojan, anti malware, crud to eat up cpu cycles


this is one reason, theres plenty more

Just wanted to say...how did you figure out spam was OS related? :D

---

### Post by phillw on 2009-10-27
> **stinger30au said:**
> no antivirus, anti spam, anti trojan, anti malware, crud to eat up cpu cycles


this is one reason, theres plenty more


::cries::

Has ClamAV running on my mail server, along with SpamAssassin ....

LOL

With a my full lamp installation and mail-server booting to log-in screen and onto my desktop (Yeah, I have the full GUI on my machine !!) In about a minute on a laptop with a celeron M 440, 1GB RAM - I'd say it's a bit fast - still beats the windows XP machine sat next to me !!!

:popcorn:

Yay, guyz & galz in development - I take hat off to you !!!

Phill.

---

### Post by chiwi on 2009-10-27
I had Ubuntu 9.04 and recently updated to 9.10 Beta, but I have not seen any boot-timing improvement at all.

I've read that ext4 and grub2 are only installed on fresh systems, not in upgrades. Does this have something to do with the boot time improvement?

This is running on a relatively new computer, Core2Duo and 4gb Ram.

---

### Post by lemming465 on 2009-10-28
Grub2 no, since not much time is spent in the boot loader before the kernel initializes.

Ext4 maybe, but you wouldn't see the real benefit unless you installed from scratch on a freshly formatted filesystem.

Most of the work is in reduced device delays and application improvements (kernel, upstart, X, ...).

---

### Post by chiwi on 2009-10-28
is ext4 **that** fast? should I consider backing up several GB of Music/movies/pictures in order to install everything from scratch ?

how much faster is it ? 10% ?.....40% ?

---

### Post by SuperSonic4 on 2009-10-28
Not really

---

### Post by lemming465 on 2009-10-28
In general ext4 performs about the same or slightly faster than ext3, but your mileage may vary.  A fresh ubuntu install onto a newly formatted ext4 filesystem will probably install slightly faster than onto ext3 (5%?) and might boot slightly faster (3%?), but won't be noticably different for light use like web browsing.

* mount time options matter; write performance of ext4 with barriers on by default will be slower than ext3 with barriers off by default

* in response to ext4 R&D, recent Linux kernels are changing *ext3* more than you'd expect; if distributions change their ext3 mount parameters in response, next years ext3 benchmarks won't match this years

* usage matters.  A fresh ext4 filesystem allocates inodes that are twice as big as ext3.  If you use ACL's a lot (Samba server with windows domain clients?) or SeLinux labels (redhat enterprise?), the improved locality of reference in ext4 will give a noticable performance boost to some workloads.  Extent based allocation means than ext4 deletes large files very much faster than ext3; if you are working with video editing this might matter.

In disk benchmarks and in parallel programming, there are very few universal performance wins: it almost always matters deeply what the usage pattern is.  E.g. read-heavy disk workloads do fine on RAID-5 layouts, but write heavy workloads suffer a 4x penalty.  If you have a write-heavy database workload your design response is to double the cost of the redundant disk system and use striped mirrors (RAID 1/0) instead.

If you like to keep up with the Jones, use ext4 - it's newer and shinier.  If you need to work with large files regularly, where large is from 500MB to any number of terabytes, definitely use ext4 over ext3.  Otherwise flip a coin.

---

### Post by Tomatosoup on 2009-10-28
It does certainly boot fast, Karmic Koala with a fresh ext4 partition. :)

---

### Post by winotree on 2009-10-28
> It does certainly boot fast.... Yes, it does.  I used a new profile on my clean-install *and* am trying one of the prerelease Firefox browsers -- the total effect is much like a new computer.  That's something I can get used to.  :D

---

