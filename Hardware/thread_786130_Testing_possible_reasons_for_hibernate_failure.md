---
title: "Testing possible reasons for hibernate failure"
date: 2008-05-07
forum: Hardware
---

### Post by asundaresan on 2008-05-07
Hi:

I'm a fairly experienced Linux user (having used redhat 7.3, gentoo, etc) and I am currently flummoxed by a hibernate problem on my Thinkpad T60. It just worked since dapper. I upgraded both my T43 and T60 laptops to Hardy Heron. On the T42, it works fine (with some noisy beeps), but on the T60 it just completely failed. This is very puzzling and I think it is not a problem with hibernate per se but some other issue which is causing it to break. 

**The problem:**

When I hibernate, it makes all the hibernate light blinks and it behaves quite normally. However, when I restart the machine, it is like a fresh restart. 

**System specifications:**

I do not have any proprietary drivers installed on the laptop. It was however upgraded from dapper and not a fresh install. Due to a number of customizations (this is my work laptop) I'd much rather not do a fresh install. But hey, what can be fixed by a fresh install should be able to be fixed by other means. 

Does anybody know which scripts are run to hibernate, so that I can go through them to try find out the problem? For instance, there is a package called hibernate and uswsusp neither of which are installed. There are a number of scripts in /etc/hibernate/ but I don't know which ones are used. Is there any information anywhere that I can use? 

I was surprised that there are not any wikis or how-tos which detail the hibernate procedure and to trouble-shoot it.

Thanks very much,
Aravind.

---

### Post by asundaresan on 2008-05-08
I finally found a solution to this problem. I think it must have been caused by the upgrade from dapper to hardy heron although I am not sure. I got the solution from a different problem which was  [fixed]("http://http://ubuntuforums.org/showthread.php?t=417964&page=3").
I saw that the file ```
/etc/initramfs-tools/conf.d/resume
``` 
is supposed to contain a line with the correct swap partition.

```
RESUME=/dev/sda3
```

Instead what I found is

```
RESUME=
```

I updated it and did a "update-initramfs -u" and rebooted and now it works! I don't know whether the upgrade caused this though that is the most likely cause. I even tried ```
dpkg-reconfigure linux-image-generic
``` and also with other packages, but that led nowhere.

But the fact that it took me so long to find the solution to a simple problem led me to think that there must be some wiki or documentation which can help trouble shoot such problems. Is there any such wiki?

---

