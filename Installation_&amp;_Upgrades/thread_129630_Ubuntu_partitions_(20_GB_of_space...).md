---
title: "Ubuntu partitions (20 GB of space...)"
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

### Post by Robgould on 2006-02-14
wow....that sounds complicated.  I usually just run the install cd and let Ubuntu handle the partitioning.  I have never had a /boot partition or a /root partition or a /usr partition or a /home partition.  I have read about people using them, but I don't think I have ever heard anyone wanting as many partitions as you do.  You are talking about 6 partitions, thats crazy.  The two special partitions I have seen talked about he most are /boot and /home.
 
Good luck.

---

### Post by lha on 2006-02-14
[QUOTE=chrisav]Hello, I am decided to install ubuntu on a computer that had windows 98 on it.
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
Chris.[/QUOTE]

Easiest (and usually the best for beginners) is to let installer automatically partition. It will create a swap and root. (Root = /)

If you decide to create partitions manually, the order isn't relevant. For linux, it doesn't matter much whether a partition is primary or logical. I'd say /root shouldn't be on a separate partition; there's hardly any use for it. /boot is useful to have if your bios is old and cannot boot from partitions beyond certain limit. Rember that / and root are the same thing, but /root means something else. ~500MB sounds like a good size for swap.

---

