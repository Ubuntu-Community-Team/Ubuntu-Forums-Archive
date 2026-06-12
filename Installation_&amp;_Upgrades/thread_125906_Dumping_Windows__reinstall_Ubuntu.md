---
title: "Dumping Windows / reinstall Ubuntu?"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by uneasyjd on 2006-02-05
After a month with Ubuntu I'm ready to dump Windows for good.  I'm currently dual-booting as follows...

6GB hard drive (master) - Windows XP by itself
6GB hard drive (slave) - Ubuntu by itself

What's the best way forward - should I freshly install Ubuntu on my master and reformat my slave for storage, or should I change the jumpers, etc. to make my current Ubuntu drive the master and zap the Windows drive?

(If the 2nd option is best, could someone walk me through it?)

---

### Post by jasmuz on 2006-02-05
If i where you, i would take the easy way out...

Just reformat your primary HD and place it has /home

---

### Post by taurus on 2006-02-05
Yes, I would also recommand do it the right way.  Install Ubuntu on the first HD and mount the second HD as /home.  No need to play around with all the cables and jumpers.

---

### Post by Jedeye on 2006-02-05
I dumped Windows just last week... I reinstalled b/c I was dual booting on my primary and then formated my secont HD as ext3. Worked good for me... and since your secondary is allready a linux file sytem you would only have to install on your windows drive.

---

### Post by taurus on 2006-02-05
[QUOTE=Jedeye]...and since your secondary is allready a linux file sytem you would only have to install on your windows drive.[/QUOTE]
If you don't format the second harddrive, then you would have two copies of Ubuntu!!!  :-k

---

### Post by lha on 2006-02-05
[QUOTE=uneasyjd]After a month with Ubuntu I'm ready to dump Windows for good.  I'm currently dual-booting as follows...

6GB hard drive (master) - Windows XP by itself
6GB hard drive (slave) - Ubuntu by itself

What's the best way forward - should I freshly install Ubuntu on my master and reformat my slave for storage, or should I change the jumpers, etc. to make my current Ubuntu drive the master and zap the Windows drive?

(If the 2nd option is best, could someone walk me through it?)[/QUOTE]

Easiest solution is to reformat (and maybe even repartition) your Windows drive and then edit fstab to get new partition(s) automatically mounted at startup. Reinstalling or swapping drives' locations cause you more work. In case you manage to overwrite mbr on Windows drive (ie erase grub), [see this thread how to restore grub]("http://ubuntuforums.org/showthread.php?t=76652").

---

### Post by uneasyjd on 2006-02-05
Thanks for the advice - I'm going to zap Windows and do a new Ubuntu installation on my hda.

I don't suppose anyone could quickly tell me how to sort out my hdb as my new /home...

---

### Post by lha on 2006-02-05
[QUOTE=uneasyjd]Thanks for the advice - I'm going to zap Windows and do a new Ubuntu installation on my hda.

I don't suppose anyone could quickly tell me how to sort out my hdb as my new /home...[/QUOTE]

I assume you have selected automatical partitioning for hdb when you installed Ubuntu, so you have two partitions on hdb. The bigger one is used as / and the smaller one is used as swap. They give you a good guideline on what sizes your new partitions on hda should be. Set the bigger one's mount point at / and set the smaller to be swap. Then delete partitions on hdb and create one big partition on it. Set it's mount point to /home.

When you create /home partition, set 'reserved blocks' to 0%. This will make all space on /home accessible to you as normal user. (Normally 'reserved blocks' is set to 5%, reserving 5% of every ext3-type filesystems to root. As neither root user or system doesn't need anything on /home, you can safely give all space on that partition to users. If you used 5% 'reserved blocks' you would "lose" 300 MB from your /home.)

If you want, you can switch places of your hard drives. After that, you could use the existing partitions for / and swap and create a partition on the other drive to used as /home. (Remember to format /.)

See [http://users.bigpond.net.au/hermanzone/p14.htm]("http://users.bigpond.net.au/hermanzone/p14.htm") details on manually editing partition table.

---

