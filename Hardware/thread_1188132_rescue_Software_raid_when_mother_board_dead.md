---
title: "rescue Software raid when mother board dead"
date: 2009-06-15
forum: Hardware
---

### Post by csyckad on 2009-06-15
I use 2 harddisk build up software raid when i install ubuntu,
now, the motherboard crash, i plug the harddisk to another pc and use ubuntu 9.04 live CD to boot up, it can detect the harddisk ,
but cannot detect the partition.


I search in google and follow [this]("http://andrewsblog.org/2008/11/16/mounting-a-linux-software-raid-array-lvm/")
but i cannot modprobe dm-mod (no this module)
and "mdadm --examine /dev/sda1" nth output,

please help. thanks

---

### Post by ronparent on 2009-06-15
The live cd doesn't have mdadm. You should use the alternative cd which has the raid software. You can do a temp install of mdadm in a live cd session. Although the install is good only for the duration of the session it would allow you to see the software raid. ie **sudo apt-get install mdadm**

---

### Post by csyckad on 2009-06-15
i install the mdadm,
but it said no raid when i mdadm --examine /dev/sda1

any ideas?

---

### Post by csyckad on 2009-06-21
after i follow this [article]("http://www.linuxjournal.com/article/8874"),
i can see the raid, but because my LVM on raid, so i cannot recover my data up to now.

i can see my raid on /proc/mdstat

even I pvscan and lvscan it shows nothing.
I cannot see any volumn group .
Does anyone know it?

---

