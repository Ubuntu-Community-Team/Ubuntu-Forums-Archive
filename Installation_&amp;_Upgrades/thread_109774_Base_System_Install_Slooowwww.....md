---
title: "Base System Install Slooowwww...."
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by GXP on 2005-12-29
Second attempt at 5.10, with same issue.

Last evening tried to install Ubuntu for the first time, all went well until 'Installing the base system" (the one after Partition Config) and was stuck on 6% - it was working - just very slow. I watched a movie and came back still at 6%, seems to be taking 5+ minutes per package. Turned off the machine when I went to bed.

This morning started a *new* install and after 50 minutes "Installing the base system" at 6%, currently working on 'ifrename...', previous was bsdutils which took over 10 minutes.

All of the other parts were quick, CD-Rom install, network detection. This is a bit frustrating. Previously had CentOS on the machine, but not skilled enough to try to recompile kernel to change CONFIG_NET_ISA=n to =y to use my network card. Wasn't that impressed with it either. Have been wanting to use Ubuntu for sometime, so finally taking the plung.

Burned to CDRW, possible need to burn to CDR? I was able to veiw the contents of all of the dir's. Any suggestions on why this is so painfully slow?

---

### Post by ShirishAg75 on 2005-12-29
Two things first, can u post u'r machine config. here alongwith memory specs.  Also if u got it from ubuntu's shipit then u should also have an Live CD. How u'r experience with that. Another thing that u could do is check u'r hard disk for problems. Another thing that u could try perhaps is Herman's answer to my query which is posted here [http://www.ubuntuforums.org/showthread.php?t=109017](http://www.ubuntuforums.org/showthread.php?t=109017) check for state of u'r hard disk. It might 've developed bad sectors or might be failing. That's all for now.

---

### Post by FLeiXiuS on 2005-12-29
What are the specifications of your systems hardware?

---

### Post by GXP on 2005-12-29
Dell XPS PII 333
128Mb RAM
IBM 8.5Gb HDD
NEC 32x CD-ROM


Up until 3 days ago was running XP SP2, CentOS4.2 for 2 days.

---

### Post by ed_d on 2005-12-29
Well it may run slow due to the system specs, but I had issues with a cdrw as well. Try burnig a cd-r at 4x and see what happens.

That might fix it.

---

### Post by GXP on 2005-12-29
Did the parted check and the partitions were OK.

Restarted the install again, this time turning off the external USB drive. Now the packages are taking 25 seconds each instead of 10+ minutes each. Going to try cdr instead of cdrw.

---

### Post by GXP on 2005-12-29
Problem resolved. Burned to cdr, packages were loaded in a few minutes.

Thanks for the help.:cool:

---

### Post by ShirishAg75 on 2005-12-29
USB is something these guys are working on just some more time I guess, maybe we see a good implementation in 2.6.15 :)

---

