---
title: "Expert needed - Ubuntu partitions"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by chrisav on 2006-02-14
Hello, I am decided to install ubuntu on a computer that had windows 98 on it.
I want my mother to learn how to use openoffice.org, thunderbird and firefox on it.

This computer is a pentium4  900 Mhz with 256 MB of RAM and 20 GB of free space.
I suppressed win 98 that I don't use anymore and Edulinux also (I also tried mandrake 10 before on the same computer and after on a laptop but I never used them really, I even tried to install freebsd at first some time ago on this computer but there were compatibility issues during installation).

I would like to use the entire space or almost.
I have seen that it would be good to have at least these partitions in this order :
 /, swap, /usr, /var , /home

Does the swap partition have to be before the / partition? Is it better?
Are /root and /boot partitions also (really) needed?
What is the /var partition necessary for?

With 19-20 GB of space what would be a good partitioning to begin with for a normal use? The space for each partitions?

The swap should be 500 - 512 MB?
Should the / partition be physical and the others be logical partitions on an extended partition?

Thanks in advance for all the advice.
Chris.

---

### Post by heimo on 2006-02-14
[quote=chrisav]I want my mother to learn how to use openoffice.org, thunderbird and firefox on it.[/quote] :cool:

[quote=chrisav]Does the swap partition have to be before the / partition? Is it better?[/quote]
No. Theoretically - and even then it's just good for the swap partition and worse for /. So it probably doesn't matter at all. Why is it better to place partitions in some specific order? Outer parts of disk (beginning) are the fastest.

[quote=chrisav]Are /root and /boot partitions also (really) needed?[/quote]
No. They don't usually need to be on own partitions, especially /root can be on / partition. Some people like to create separate partition for /boot. It's not neccessary.

[quote=chrisav]What is the /var partition necessary for?[/quote]
All kinds of spools (mail, printer...) and web server files and databases are typically located there. VARiable stuff.

[quote=chrisav]With 19-20 GB of space what would be a good partitioning to begin with for a normal use? The space for each partitions?[/quote]
5GB for /, 512MB for swap, all the rest for /home. No other partitions.

[quote=chrisav]The swap should be 500 - 512 MB?[/quote]
Yeah, that's ok. 1,5-2x memory is a rule of thumb.

[quote=chrisav]Should the / partition be physical and the others be logical partitions on an extended partition?[/quote]
 Doesn't matter. I pretty much always make first three partitions primary and if needed, rest partitions as logical (on extended).

---

