---
title: "how come disk size is less than what is specified"
date: 2009-04-04
forum: Hardware
---

### Post by ubantuwannabe on 2009-04-04
when I do df -h

doordie@doordie-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             285G  9.6G  261G   4% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  156K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile

if u do ure maths the total size is only 294G which is way much less than what is specified in the receipt.

It is not a dual boot system. laptop is hp nc6600 and when I purchase the laptop it is stated in the receipt that it should be 320G,

so why the 26G different?

also if 30G is allocated to ntfs, will the command show the ntfs partition?

when I purchase the laptop it is in windows xp, and when I partitioned the system using ubuntu 8.10 installation disk the before partitioned image does not show any ntfs partition if I did not remember wrongly.

is there anything I'm missing?

many thanks!

---

### Post by squaregoldfish on 2009-04-05
Welcome to the world of lying hard drive manufacturers. In computer land, 1 megabyte is 1024Kb. Hard drive manufacturers claim that 1 megabyte is 1000Kb. This means that what the drive says it will hold is more than what the OS will tell you.

Steve.

---

