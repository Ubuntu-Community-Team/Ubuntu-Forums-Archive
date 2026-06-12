---
title: "Some clarification questions about mounting home on a partition"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by woodenanteater on 2009-04-11
Hey guys,

I'm running a clean install of ubuntu 8.10, and I'm following a set of instructions which refer to mounting my home directory on a formatted, pre-existing partition (which I've created already) after installation.  However, in the installation wizard, it gives you the option of designating a partition for mounting the home directory, which I did (so in that step I selected mount points for both / and /home).  I would have thought that this would do the job for me, but when I look in my root folder, home is still there, and it appears this is where everything (documents, and such) is going.

I'm obviously misunderstanding the process, so could someone give explain the process a bit better?

Many thanks.

---

### Post by Elfy on 2009-04-11
IF you gave / and /home seperate partitions that is what you should have. If you look in / then you will see /home, in the same way that I have completely different hdds showing up in /mnt

From a terminal run df -h

See if /home is on a different partition to /

Mine looks like, I don't have a seperate home

> [COLOR="Red"]/dev/sdc5[/COLOR]             9.6G  4.4G  4.8G  48% /
tmpfs                 628M     0  628M   0% /lib/init/rw
varrun                628M  348K  628M   1% /var/run
varlock               628M     0  628M   0% /var/lock
udev                  628M   96K  628M   1% /dev
tmpfs                 628M   88K  628M   1% /dev/shm
lrm                   628M  2.4M  626M   1% /lib/modules/2.6.28-11-generic/volatile
[COLOR="Red"]/dev/sda5 [/COLOR]             54G   49G  4.9G  91% /mnt/data
[COLOR="Red"]/dev/sdb2 [/COLOR]             74G   55G   18G  76% /mnt/media
[COLOR="Red"]/dev/sdc3 [/COLOR]            126G   95G   30G  77% /mnt/music

---

