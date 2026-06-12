---
title: "Can't see partitions in gparted"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by psyncho on 2009-07-10
Hi, I'm trying to figure out my partitions and what I should do, if anything, to fix them, or figure out what's up with them. Any feedback is appreciated. 

I have Ubuntu 8.4 on a box with an SATA drive. I installed it sometime ago so don't remember what I did for partitions. Recently I got a synaptic error message that /boot was full so I went to try and look at the partitions and gparted reported:

/dev/sda1 ext3 /boot  243 MiB
/dev/sda2 extended
/dev/sda5 uknown

Can someone please tell me how I would get more info? Is this normal? I originally had thought to resize my /boot partition, but now I'm not quite sure what's going on. The only think I can imagine is that I defaulted to use only one partition on install, and that this is some side effect of that setup (I used to manually partition everything).

df gives me:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/pythia-root
                     304552248  46116700 242965164  16% /
varrun                  484976       248    484728   1% /var/run
varlock                 484976         0    484976   0% /var/lock
udev                    484976        56    484920   1% /dev
devshm                  484976         0    484976   0% /dev/shm
/dev/sda1               241116    197058     31610  87% /boot

My fstab is:
proc /proc proc defaults 0 0
/dev/mapper/pythia-root / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=19569121-6c83-4f01-b8ab-7db667dc2a56 /boot ext3 defaults 0 2
/dev/mapper/pythia-swap_1 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

None of that really helps me or even looks familiar from my manual partitioning days.

thanks

---

### Post by buckrodgers on 2009-07-15
Use ```
fdisk /dev/sda
``` 

The p command allow you to print the partitions on your HD 
The q command to quit

**DO NOT USE ANY OTHER COMMANDS as it might endanger your data**

If you use ```
df -h
``` it will print the sizes in human readable form which is more convenient.

Cheers

---

