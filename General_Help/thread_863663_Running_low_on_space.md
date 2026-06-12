---
title: "Running low on space"
date: 2008-07-18
forum: General Help
---

### Post by alistair23 on 2008-07-18
Ubuntu says that i am running low on space on my partion. But i'm not. I have lots of external and internal hard drives mounted, and they appear in Media so on a 28GB drive i have used 298.5GB so is there a way i can say, there not counted i'm not running low on space.

---

### Post by avtolle on 2008-07-18
What matters here is the size of the partitions, not the total size of the HDD. If, e.g., a partition is 5GB, once that 5GB is full, it matters not that there may be 100 GB available elsewhere on the HDD.

Post the results of```
df -h
```so someone can take a look.

---

### Post by sandeepy on 2008-07-18
Could you please elaborate your problem ? As far as mounting is concerned, you would not have that included in your "used" space.

---

### Post by cdtech on 2008-07-18
How do you have your install partitioned? Type on a command line "df -H" to see the available space on all partitions. You may have your root partition set to small.....

---

### Post by cdtech on 2008-07-18
> **avtolle said:**
> What matters here is the size of the partitions, not the total size of the HDD. If, e.g., a partition is 5GB, once that 5GB is full, it matters not that there may be 100 GB available elsewhere on the HDD.

Post the results of```
df -h
```so someone can take a look.

Sorry avtolle, we must have bumped heads on the reply. :)

---

### Post by alistair23 on 2008-07-18
> **avtolle said:**
> What matters here is the size of the partitions, not the total size of the HDD. If, e.g., a partition is 5GB, once that 5GB is full, it matters not that there may be 100 GB available elsewhere on the HDD.

Post the results of```
df -h
```so someone can take a look.

The results are
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sdb5              26G   25G  484M  99% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   72K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       26G   25G  484M  99% /home/alistair/.gvfs
/dev/sdc1             233G  196G   38G  85% /media/BACKUP
/dev/scd0             7.8G  7.8G     0 100% /media/cdrom0
/dev/sda5             6.4G  1.9G  4.6G  30% /media/Share

```

My problem is that mounted partions count towards my total size and my used space.

---

### Post by alistair23 on 2008-07-18
Sorry. I am an idiot. theres nothing wrong. sorry.

---

### Post by avtolle on 2008-07-18
No, your problem is that the partition mounted on /dev/sda5 (which is your root partition) is 99% full. You need to clear it out a bit to get some more room there. 

Since you have no separate /home, the / partition holds the OS, the kernel, and all your data files.

---

### Post by cdtech on 2008-07-18
> **alistair23 said:**
> Sorry. I am an idiot. theres nothing wrong. sorry.

No idiot's here.

You do have problems but none that cant be fixed.

---

### Post by alistair23 on 2008-07-18
How can i get more space?? What can i delete

---

### Post by cdtech on 2008-07-18
> **alistair23 said:**
> How can i get more space?? What can i delete

Maybe downloads that pile up or even kernel versions you don't use, eat up a lot of space. Use an external share drive for your music, videos and pictures.

It's easy for me to tell you to delete stuff, but I don't know what you have in your setup, that's up to you really.

---

### Post by hyper_ch on 2008-07-18
```

sudo apt-get autoremove
sudo apt-get autoclean

```
that should free (some) space

---

### Post by avtolle on 2008-07-18
Well, one thing to try is (from the terminal)```
sudo apt-get clean
```to clear the cache of stuff left over from installing various applications. If you have multiple media players installed, and aren't using all of them, you could remove the ones you don't use. Those are just two suggestions, there are other things (do you have backup files that could be deleted? you might try. 

Finally, if there is adjacent available space on the HDD, you could resize by enlarging the root partition (you will need to do this with a live cd, as the partition cannot be mounted when work is being done upon it, and if booted from the HDD, that partition will be mounted and cannot at that point be unmounted). 

Good luck.

---

