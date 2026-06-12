---
title: "Swap file does not initilize on startup"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by danielph on 2005-12-13
After installation of 5.10 I noticed that my swap was only 100MB (my fault I think). The RAM on this machine is only 256MB. The problem this caused, which I have lived with for a couple of weeks now, is that the system ground to a halt when too many apps where open. Looking at my options I decided to create a swap file (not a partition) on one of the existing partitions. Here are the steps I took:


dd if=/dev/zero of=swapfile1 bs=1024 count=1048576
/sbin/mkswap -c -v1 swapfile1
/sbin/swapon /media/reiser/tmp/swapfile1

This works very well and no more system lock ups. The results:

root@moroco:/home/danielph#
Filename                                Type            Size          Used    Priority
/dev/hda2                               partition       104412    104404  -1
/media/reiser/tmp/swapfile1   file                1048568  119664  -2

(the swapfile is is on hdb1)

The problem I have is how to keep this situation after a reboot. I tried fstab adding this line:

/dev/hdb1/tmp/swapfile1	none	swap	sw	0	0

but I get the feeling that fstab wants a partition.

I believe there must be an init file somewhere where swapon can be run. Any suggestions would be helpful. Is there a system startup file for running stuff like this or for even running apps?

and finally is this a good way to do this (as a file not a partition)?

thanks in advance

Dan

---

### Post by danielph on 2005-12-15
Has anyone got an answer for this? Or maybe someone could tell me how to run programs at startup? If I could just run swapon at startup it would solve the problem.

thanks in advance 

Dan

---

### Post by danielph on 2005-12-16
It was a simple mistake. I have found the answer to this and here it is:

Fstab should read

/media/reiser/tmp/swapfile1	none	swap	sw	0	0

not 

/dev/hdb1/tmp/swapfile1	none	swap	sw	0	0


For partitions use /dev, but for swapfile use the mounted name

---

