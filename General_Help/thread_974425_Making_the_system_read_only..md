---
title: "Making the system read only."
date: 2008-11-07
forum: General Help
---

### Post by lhong1987 on 2008-11-07
I have recently purchased Asus eee pc 900a.
I installed ubuntu eee and I am now messing around with it.

As you might know already, eee 900a uses solid state drive.
I read that to has a limited number of write/erase capability so I was thinking I might make the whole system read only and save all data in external drive.

first question, is that a bad idea?

I have thought about modifying fstab and making my root partition read only, but i realized that I might want to upgrade once in a while, and that might be a pain if the root were read-only.

Is there a way to make the partition read-only by default and change it read-write only for su or only at specific time?

or a way to modify a grub so that one option loads the partition as r/o and second as r/w?

I know it's very specific and odd question to ask, but help would be much appreciated :)
Thanks in advance.

---

### Post by Sam on 2008-11-07
You should not do that, there are always files that needs to be updated by the system (in /home, /var, /tmp, ...). However some directories are not willing to change without your intervention (/bin, /usr, /lib, ...). If you place them in specific partitions, use "ro" (readonly) flag in fstab.


BUT

You can make less disk I/O by tweaking your fstab, eg: [adding "noatime"](http://ubuntuforums.org/showthread.php?t=692318).

---

### Post by lhong1987 on 2008-11-07
well, then how does the live CD work?
i was thinking close to the line of how live CD works except I can modify it once in a while.

---

