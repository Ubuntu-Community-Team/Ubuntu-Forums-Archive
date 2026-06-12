---
title: "hard drive space all weird"
date: 2008-12-27
forum: Hardware
---

### Post by outcesticide on 2008-12-27
hay can anyone help me with my hard drive space i checked my entire computer and it says it only has 60.78 gb on it and it only has 5.8 gb of free space but i know for a fact it has a total capacity of 180gbs, so whats up with that?

---

### Post by mariner09 on 2008-12-27
At a command prompt, type df and post it here.
 
Also, the output of more /etc/fstab.

Maybe you have a 180gb drive, but when you installed Ubuntu, it only created a 60gb partition.

---

### Post by outcesticide on 2008-12-27
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  131G  5.7G  96% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  316K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  236K  500M   1% /dev/shm
lrm                   501M  1.2M  499M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb2              28G   23G  5.5G  81% /media/ERIC'S IPOD
/dev/scd0             700M  700M     0 100% /media/cdrom0

oh and when i installed it, it was 180 i also have checked pretty often, and it just happened today after i installed a few programs in synaptic.

---

### Post by outcesticide on 2008-12-27
oops srry my original size was 150 not 180 srry

---

### Post by DoctorBeaver on 2008-12-27
This is a thread I started some time ago [http://ubuntuforums.org/showthread.php?t=976335]("http://ubuntuforums.org/showthread.php?t=976335")

---

### Post by mariner09 on 2008-12-27
Can you think of anything that might've changed in between reading the disk usage?  Did your iPod sync with different locations?  Might be the case if you started with one music app and then switched to another.

Are you the only user on your system?

Whenever I build a system, I always have / and /home as separate partitions so that the system will always be usable if I have drive space issues.

I can only guess that you have a ton of songs or other media files on your system.

---

