---
title: "Bootchart will not install!!"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by ssalman on 2005-12-11
Hi,
 I'm trying to improve my laptop boot time, and my 1st step is to install Bootchart pkg, so I can measure boot time improvements when I change various things. So far I was able to install all it's dependencies successfully, but I get the below error when trying to install Bootchart it self.

 I'm using the two Ubuntu supplied kernels (386&686), and they both have the same issue. I have no idea why it is complaining about this... does anybody have a clue??

Thanks.

```

$ **sudo dpkg -i bootchart_0.9-0ubuntu4_all.deb**
Password:
(Reading database ... 59076 files and directories currently installed.)
Preparing to replace bootchart 0.9-0ubuntu4 (using bootchart_0.9-0ubuntu4_all.deb) ...
Unpacking replacement bootchart ...
Setting up bootchart (0.9-0ubuntu4) ...
/boot/initrd.img-2.6.12-9-686 was been altered.  Cannot update.

```

---

### Post by ranf on 2005-12-11
That is the version from Dapper, isn't it?
I've installed version 0.8-3 (from Debian IIRC). Installed fine and worked fine.

---

### Post by ssalman on 2005-12-12
Thanks ranf!  I tried the Debian package (version 0.9-1) and it worked great, I don't know why it is different from the Ubuntu version!!

The good news is - I was just able to reduce my boot time from 59sec to 52sec by just switching from the 386 kernel to the 686 kernel, that's a 12% reduction!! will try other things next.

Thanks again.

---

### Post by ranf on 2005-12-13
Have you seen these HowTos:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=80423](http://ubuntuforums.org/showthread.php?t=80423)

---

### Post by ssalman on 2005-12-13
I'm working on them now... Thanks :)

---

### Post by soongwoo on 2006-04-09
[QUOTE=ranf]That is the version from Dapper, isn't it?
I've installed version 0.8-3 (from Debian IIRC). Installed fine and worked fine.[/QUOTE]

I'm using Ubuntu 5.10. How can I install bootchart 0.8-3 for Breezy?

Thanks
soongwoo

---

### Post by ranf on 2006-04-10
Search for it on:
[http://packages.debian.org](http://packages.debian.org)

---

### Post by soongwoo on 2006-04-10
Thansk, ranf.

soongwoo

---

