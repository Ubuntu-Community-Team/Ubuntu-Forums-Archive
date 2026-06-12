---
title: "HDD Allocation Order 8.04"
date: 2008-05-07
forum: Hardware
---

### Post by auskento on 2008-05-07
I have a Ubuntu 8.04 server setup and want to force the way in which drives (/dev/sd*) are allocated.

I have a motherboard with a single HDD attached to the onboard controller that i want to force to be /dev/sda.

Recently however, I have added a 3ware 8506-12 controller to the system and connected 4 1TB drives to it.  These drives take allocation as /dev/sda-d and I'm sure when I add the next lot of drives to the system, they will become e-h.  Currently, the single boot drive has been allocated /dev/sde and this has made system bootup slow and has also screwed with the software raid configuration becoming invalid (having been initially created as /dev/sd[bcde]1

Any pointers on how to change the order in which controllers / drives are allocated?

---

### Post by Invader Amoto on 2008-05-07
Hello,
I'm not positive that this is what your looking for, but you could always edit /etc/fstab but make sure u use UUID of the drive instead of its /dev/sd** location because the UUID never changes.
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

-Invader Amoto

---

### Post by auskento on 2008-05-07
uuid is already being used, and its fine for static partitions.

Its the raid array configuration thats having problems because the allocation gets changed.

---

### Post by zerosub on 2008-11-12
hi auskento,

did you find a solution to this problem?
I'm having the exact same problem.

i have a 120GB HDD connected to the onboard IDE controller as System disk.
Then there are 4 SATA drives connected to a PCI 4 Channel S-ATA controller.

the raid5 should be on /dev/sdb,c,d,e ...
but every 3rd Boot , Ubunu decides to put the IDE HDD as /dev/sde and the raid won't start...

This really is a pain in the a...

anybody else with a suggestion ?

ps: i'm already using UUIDs in the fstab , but that doesn't help for mdadm assembly :(

---

### Post by ebichete on 2008-11-12
Have you tried using disk labels ? Then you can replace /dev/sd? with LABEL=HOME_1 and LABEL=HOME_2.

```
mdadm --create /dev/md0 --level=0 --raid-devices=2 LABEL=HOME_1 LABEL=HOME_2
```

I've never tried this myself, but it seems logical. Unless, of course, that mdadm has no support for disk labels.

---

### Post by zerosub on 2008-11-13
after days of trying to find a solution , i think the order of the drives now stays the same.
I used the information from this thread [http://ubuntuforums.org/showthread.php?t=483276](http://ubuntuforums.org/showthread.php?t=483276)

especially this was what helped me out:

```
--So I modified " /usr/share/initramfs-tools/modules " and added " ata_generic " at the end so it loads the motherboard SATA driver first.

--Then I had to regenerate the initramfs:

' update-initramfs -u '
' reboot '

```

after 5-10 reboots , i did not have the problem.
Hopefully it will last ...

thanx for your help anyway.

---

