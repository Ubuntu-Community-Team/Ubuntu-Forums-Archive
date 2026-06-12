---
title: "Hard Disk Not Showing"
date: 2009-06-02
forum: Hardware
---

### Post by Apoorvbarwa on 2009-06-02
i am running ubuntu 9.04 intrepid and have two hard disks 
80 gb Pata 
250 gb Sata
i had successfully installed the two hard disks but today i switched on Xp for a while and after that my 250 Gb hard disk is showing as a Mass Storage Device and cannot be mounted. plz help i hav a lot of data in that hard disk which i dont want to loose

---

### Post by lisati on 2009-06-02
Did Windows shut down properly? Odd things can sometimes *seem* to happen if it dosn't. One workaround is to log into Windows and then shut it down again.

---

### Post by Apoorvbarwa on 2009-06-02
yes windows shut down properly... but the thing is i can see my hard disk listed in bios......but not in ubuntu....... i searched for my problem and found a command df which on typing............
apoorv@apoorv-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             14428928   6869004   6826960  51% /
tmpfs                   511896         0    511896   0% /lib/init/rw
varrun                  511896       212    511684   1% /var/run
varlock                 511896         0    511896   0% /var/lock
udev                    511896       152    511744   1% /dev
tmpfs                   511896       520    511376   1% /dev/shm
lrm                     511896      2392    509504   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             10241404  10235924      5480 100% /media/disk
/dev/sda5             30716248  30710456      5792 100% /media/New Volume
/dev/sda8             20988888  19308676   1680212  92% /media/disk-1
i dont know what this command does but this is what i got plz tell me what this means and how can i rectify this problem

---

### Post by Apoorvbarwa on 2009-06-03
guys i got the hard disk to work.......what i did was changed the slot on the motherboard to which it was connected... but even so i dont understand how this happened as no matter which slot i connected it to it always showed the hard disk in the bios but not in ubuntu...which led me to believe that the slots on the motherboard are fine..... but then why would it not show in ubuntu..... and on the last slot it worked with ubuntu..... can anybody explain why this happened.. i really want to know... and if this is of any help..prior to my problem starting i had installed KDE...i already had GNOME(pretty obvious)...but thats all i had done......please tell me why this happened.......

---

