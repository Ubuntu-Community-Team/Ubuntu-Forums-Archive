---
title: "mdadm boot problems"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by colo on 2005-04-17
Heyho folks,

I just installed Hoary on my primary system, simply because I wanted to avoid fiddling with the installation of Gentoo for now - and a CPU-arch upgrade is due soon. Since my system boasts two shiny SATA-drives, I use to run software-RAID. So I configured / and /boot to be RAID1, and /home as well as /usr/local to be RAID0 with the Ubuntu Installer (that process is quite unintuitive imo, btw - I'd rather set that by hand next time if possible...). Everything went fine until the initial reboot, where mdadm fails to start the two RAID0-arrays, /home (dev/md1) and /usr/local (/dev/md3). I don't know why exactly, since the devices start up just perfectly normal when I manually assemble them via mdadm in maintenance-mode, or after forcing the boot-process to continue (and, besides, finish successfully!).

I really wonder why this is the case... and would highly appreciate your support on this issue, as it's annoying to issue Ctrl-D on bootup, switch terminals to a CLI-tty, login as root, manually start the md-devices and mount /home and /usr/local just to be able to log in properly via gdm. Maybe something regarding udev/hotplug is wrong?


I've included hopefully useful dmesg-output below for your viewing pleasure ;)
```
root@ubuntux:~ # dmesg | grep raid
md: raid1 personality registered as nr 3
raid1: raid set md2 active with 2 out of 2 mirrors
raid1: raid set md0 active with 2 out of 2 mirrors
md: raid0 personality registered as nr 2
raid0: looking at sdb6
raid0:   comparing sdb6(139243264) with sdb6(139243264)
raid0:   END
raid0:   ==> UNIQUE
raid0: 1 zones
raid0: looking at sda6
raid0:   comparing sda6(139243264) with sdb6(139243264)
raid0:   EQUAL
raid0: FINAL 1 zones
raid0: done.
raid0 : md_size is 278486528 blocks.
raid0 : conf->hash_spacing is 278486528 blocks.
raid0 : nb_zone is 1.
raid0 : Allocating 4 bytes for hash.
raid0: looking at sdb5
raid0:   comparing sdb5(4883648) with sdb5(4883648)
raid0:   END
raid0:   ==> UNIQUE
raid0: 1 zones
raid0: looking at sda5
raid0:   comparing sda5(4883648) with sdb5(4883648)
raid0:   EQUAL
raid0: FINAL 1 zones
raid0: done.
raid0 : md_size is 9767296 blocks.
raid0 : conf->hash_spacing is 9767296 blocks.
raid0 : nb_zone is 1.
raid0 : Allocating 4 bytes for hash.

```

Here we go with /etc/mdadm/mdadm.conf:
```
colo@ubuntux:~$ grep -v "^$" /etc/mdadm/mdadm.conf | grep -v "^#"
DEVICE partitions
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=277b6c1c:7673bfac:0e479ab7:6941bc6f
   devices=/dev/sdb3,/dev/sda3
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5dcd1c9d:da591e63:4a1171a5:706b78cc
   devices=/dev/sdb1,/dev/sda1
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=1ca2f16a:f514c369:51d2507d:21c20ca6
   devices=/dev/sdb6,/dev/sda6
ARRAY /dev/md3 level=raid0 num-devices=2 UUID=3750903f:34927618:f8479642:7e8908d3
   devices=/dev/sdb5,/dev/sda5
```

Here's with what mdadm comes up at bootup:
[Click to view (~130kb)]("http://retroms.he4d.net/pics/pic00256.jpg")

/etc/fstab appears to be flawless, and will therefore not be posted without request.

Thanks in advance for all your time and effort!

---

### Post by flipy on 2005-04-18
would'nt be easiest to map the partitions using device-mapper? since it is loaded at boot time, you just can modify the config file for it... the thing would be tweaking the initrd file to map it too (so you boot!).
As I [said](http://ubuntuforums.org/showpost.php?p=136750&postcount=1), the use of dmraid would have make it easiest for everyone!

---

### Post by PhilJess on 2005-04-18
I found that modifying fstab fixed this problem for me:

entries which used to be
/dev/md*              blah
now say
/dev/evms/md*      blah
and everything is working again.
 
I think that evms is managing this stuff now, and that mdadm is not required anymore, because I was able to run dpkg-reconfigure mdadm and turn it off, and everything still works.
 
:grin: Good Luck.

---

### Post by colo on 2005-04-18
Thanks, I'll try to do so and report in after the next time I actually reboot ;)

---

### Post by colo on 2005-04-18
Pointing the fstab entrys to /dev/evms/md/md1 and /dev/evms/md/md3 instead of /dev/md1 and /dev/md3 respectively fixed this issue. /dev/md2 and /dev/md0 work, as stated before. however, mdadm still complains about being unable to start the arrays.

---

### Post by emperor on 2005-04-29
I had a similar problem and found that the DEVICE statement in mdadm.conf must list all partions, not just the word "partions". For example:

mdadm.conf: (all one line below!)
========

DEVICE  /dev/sdb1 /dev/sda1 /dev/sdb3 /dev/sda3  /dev/sdb5 /dev/sda5 /dev/sdb6 /dev/sda6

---

