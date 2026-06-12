---
title: "Help resizing root partition"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by snakep on 2009-02-24
Hello,

I need to resize the / partition so that I can upgrade from 7.10 to 8.04 or later.  I plan to use gparted.  What are the steps I need to take?  I have gathered from reading some threads that there can be problems with grub after resizing.  I want to get this right the first time.

The results of df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             4.6G  3.7G  767M  83% /
varrun                503M   92K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   72K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   38M  466M   8% /lib/modules/2.6.22-16-generic/volatile
/dev/sda6             549M   69M  452M  14% /boot
/dev/sda3              29G  7.0G   21G  26% /home
/dev/sda1              40G   36G  3.6G  91% /media/sda1
/dev/scd0             493M  493M     0 100% /media/cdrom0

```

Basically, I want to move about 5 GB from /home (on /dev/sda3) to / (on /dev/sda2).  Windows XP is on /dev/sda1.

Thanks for any help you can offer.

---

### Post by Partyboi2 on 2009-02-24
Backup all your important stuff before working on partitions, then boot a ubuntu live cd and when you are at the Desktop open gparted (System>Admin>Partition Editor) make sure that the partitions you want to work on are unmounted. Then select sda3 and right click and select the resize option and shrink it using the "Free Space preceeding" and adjust it to the size you want. Then right click on sda2 and select the resize option and increase to use all the space available then apply the changes.

---

### Post by snakep on 2009-02-24
Thanks for the help.  I've never used gparted before, so I'm a little nervous.  I read in one thread that there is sometimes a problem with the /etc/fstab file, something about the UUID numbers changing.  How do I deal with that?

---

### Post by caljohnsmith on 2009-02-24
> **snakep said:**
> Thanks for the help.  I've never used gparted before, so I'm a little nervous.  I read in one thread that there is sometimes a problem with the /etc/fstab file, something about the UUID numbers changing.  How do I deal with that?

The UUID of your main root Ubuntu partition should not change when you resize it in gparted; you might be thinking of a swap partition for example, because resizing a swap partition will change its UUID. If you want to see in order to make sure, before you run gparted open a terminal (Applications > Accessories > Terminal) and do:
```
sudo blkid -c /dev/null
```
That will show the current UUIDs of your partitions; go ahead and use gparted to resize your partitions as desired, and then run that command again. I think you will see that the UUID does not change for any ext3 partitions that you resize (i.e. your main Ubuntu install for instance). Good luck and let us know how it goes.

---

### Post by snakep on 2009-02-25
Success!  I increased /dev/sda2 by 7 GB and changed /dev/sda3 accordingly.  More importantly, the UUID's did not change, and grub loaded perfectly.  Now I just need to run the upgrade.

---

