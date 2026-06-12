---
title: "Unable to create Partition"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by hutzelfix on 2009-01-07
Hi all,

kubuntu 8.10 on a Seagate 1 TB, Board is a gigabyte EP35-DS3L, 4 GB Ram.
Unable to create partition, on 2 different disks, 1 of them with a working XP Installation, which seemed to have been destroyed (didn't show up in list of partitions) but still boots.

Tried with a special debian-xen installation disk from c't which worked fine.

So I think it could be a driver or disk size problem?

1 month ago installation on a 500GB with a gigabyte EG31 Board was no problem at all - also no problem with 8.04 on a 1TB disk with some gigabyte G31 Board.

thanks for your thoughts

---

### Post by Noel96 on 2009-01-07
Partitions can only be created if you boot from the installation CD and use it as a LiveCD. (I'm not sure if you are using this or trying to create partitions after booting into an installation.)

---

### Post by hutzelfix on 2009-01-07
Sure - I booted from the installation DVD. It already worked with other disk sizes - and with same disk size but other version of ubuntu.

nevertheless I'm pretty sure you _can_ create partitions when you boot from an already installed system.

---

### Post by Noel96 on 2009-01-10
> **hutzelfix said:**
> nevertheless I'm pretty sure you _can_ create partitions when you boot from an already installed system.

Only if you boot from the LiveCD/DVD. 

I'm not sure that I have interpreted what you said, correctly. If I haven't, please ignore the below post.

If you have an Ubuntu version already installed and boot up using that, the computer has to use the hard drive to load drivers, etc. For partitioning or resizing of partitions, the hard drive has to be unmounted. And, if it's unmounted, it can't operate you system. The only way to keep the computer's hard drive unmounted for partitioning is to boot from an installation disk.

---

### Post by boof1988 on 2009-01-10
> **Noel96 said:**
> Only if you boot from the LiveCD/DVD. 

I'm not sure that I have interpreted what you said, correctly. If I haven't, please ignore the below post.

If you have an Ubuntu version already installed and boot up using that, the computer has to use the hard drive to load drivers, etc. For partitioning or resizing of partitions, the hard drive has to be unmounted. And, if it's unmounted, it can't operate you system. The only way to keep the computer's hard drive unmounted for partitioning is to boot from an installation disk.

The above is not necessarily true.

If there are partitions and/or space on the HDD that are not mounted (even though other parts of the disk are in-use for the os/swap) the non-used areas of the hard-disk can be partitioned etc.

Try it out if you have the extra space or an extra HDD.

---

### Post by kranny on 2009-01-10
> **hutzelfix said:**
> Hi all,

 1 of them with a working XP Installation, which seemed to have been destroyed (didn't show up in list of partitions) but still boots.



Just that your disks are not being shown up doesnt imply that your disk is damaged.Install gparted (Gnome partition manager) and see whether it recognises your both harddrives)

Unmount the respective partition Before formatting it

---

### Post by kranny on 2009-01-10
> **hutzelfix said:**
> Hi all,

 1 of them with a working XP Installation, which seemed to have been destroyed (didn't show up in list of partitions) but still boots.



Just that your disks are not being shown up doesnt imply that  your disk is damaged.Install gparted (Gnome partition manager) and see whether it recognises your both harddrives)

Unmount the respective partition Before formatting it

---

