---
title: "formatting an ubuntu partition from ubuntu"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by dyyyy on 2009-04-05
hi,
i made a mistake when installing ubuntu 8.10 on my pc,
and it installed on a third partition
i now have 
-windows
-ubuntu 7.04
-ubuntu 8.10

is there a way to remove ubuntu 7.04 from ubuntu
thanks

---

### Post by ronparent on 2009-04-05
Simply use your partition manager booted to ubuntu 8.10 to unmount and delete the ubuntu 7.04 partition. You will have to either delete out references to 7.10 in your grub boot menu or rerun the grub setup command to configure it to your current configuration. 

Note that unless you need the space, you could leave 7.04 in place. If you need the space you can use partition manager to expand your remaining partiotions to fill the remaing unallocated spave left by deletion of the 7.04 partition!

---

### Post by dyyyy on 2009-04-05
:S:S sorry i'm still a beginner
where can i find the partition manager?

---

### Post by Pasdar on 2009-04-05
> **dyyyy said:**
> :S:S sorry i'm still a beginner
where can i find the partition manager?

It's not installed on your system, install "gparted" from package manager and then run it by doing ALT + F2 and typing "sudo gparted". Be careful of what you do there, its permanent.

---

### Post by ronparent on 2009-04-05
In ubuntu 8.10 it is, om your menu bar, System> Administration> Partition Editor. You should probably read up on it's use before you try it.

---

### Post by dyyyy on 2009-04-05
hi i think i got it,
just to make sure, before i do anything silly :P
these are my partitions : 
-windows
-ubuntu 7.04
            -ext3
- ubuntu 8.10 
            -linux-swap
            -FAT32
            -ext3
            -linux-swap
            -unknown
            -unallocated
i should right click on ext3 in ubuntu 7.04 and delete it, then format the unallocated space right?

---

### Post by ronparent on 2009-04-05
Or grow one of the adjacent partitions to fill the space. Also, youneed only one swap.

---

### Post by drs305 on 2009-04-05
> **dyyyy said:**
> hi i think i got it,
just to make sure, before i do anything silly :P
these are my partitions : 
-windows
-ubuntu 7.04
            -ext3
- ubuntu 8.10 
            [COLOR="DarkRed"]-linux-swap[/COLOR]
            -FAT32
            -ext3
            [COLOR="DarkRed"]-linux-swap[/COLOR]
            -unknown
            -unallocated
i should right click on ext3 in ubuntu 7.04 and delete it, then format the unallocated space right?

Yes, just make sure it is unmounted and that you are really running hardy ("lsb_release -a" is the terminal command for checking). 

You can also delete one of the two linux-swap partitions. You can determine which one is in use by running:
```

cat /etc/fstab | grep 'swap'

```

---

### Post by dyyyy on 2009-04-05
wow thanks for the quick reply!!
it all worked well :D thank you
just for the linux swap, i executed cat /etc/fstab | grep 'swap'
and i got UUID=2e7ebbca-f4cd-4ab0-bba0-d261456c5be0 none swap sw 0 0
(one of the linux-swap is inactive and the other is active in the information > status )
i tried to delete the inactive but i got "Unable to delete /dev/sda7! Please unmount any logical partitions having a number higher than 7"

---

### Post by drs305 on 2009-04-05
That message is common. In order to deal with the repartitioning the partitions numbered higher than the one you are trying to delete have to be unmounted. Note that in gparted the higher number doesn't necessarily have to be to the right of the partition you are trying to delete. It was probably just created later, and thus has a higher number.

Often you can't unmount a partition if one or more are system partitions or data partitions currently in use. If they aren't system partitions, you can try closing out all your applications and attempt to unmount the higher partitions. If they can't be unmounted, you can to delete the partition from the livecd.

---

