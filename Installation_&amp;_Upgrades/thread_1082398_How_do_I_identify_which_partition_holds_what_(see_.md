---
title: "How do I identify which partition holds what (see screenshot)"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by inearlygaveup on 2009-02-27
I have just updated from Ubuntu 8.04 to 8.10 by using wbi and think the update may have made new partitions by spliting up my original Linux partitions.

Does this look and sound correct.

If so, how do I identify which partition holds what (see screenshot) as I would like to get rid of any obsolete Ubuntu 8.04 partitions

I duel boot with XP and realise that the first three partitions /dev/sda1,2&3 are my windows partitions.

I am still fairly new to Linux.****

---

### Post by taurus on 2009-02-27
Open a terminal and run this command.  Then, post the output here.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by inearlygaveup on 2009-02-27
Hi, Hope this helps

---

### Post by taurus on 2009-02-27
Looks like your root filesystem is on /dev/sda7 while the swap partition is /dev/sda8.  And you have /dev/sda2 (fat32/vfat) mounted to /media/ACER.

---

### Post by inearlygaveup on 2009-02-27
Can I delete 9 & 10 and the Swap sda5

---

### Post by taurus on 2009-02-27
And even /dev/sda6 unless you are using it but not currently mounted it.

---

### Post by inearlygaveup on 2009-02-27
Good - that was my next question do you know what reiserfs is on sda6

---

### Post by taurus on 2009-02-27
Reiserfs is just another filesystem that Linux uses (ext2, ext3, xfs, etc.)

---

### Post by inearlygaveup on 2009-02-27
Right

I take it that those partitions were left over when I updated................

After deleting, can I then just use Gparted to resize my remaining Linux partitions


From 4437 miles away - Goodnight and thanks for your help.

---

### Post by taurus on 2009-02-27
If you want to resize your harddrive (expand to take up the unallocated space), you have to do it from a LiveCD since you cannot resize a partition while you are using it.

If you don't have Ubuntu LiveCD, you can use GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Also, it depends on where the unallocated space is located.

```
sudo fdisk -lu
```

---

### Post by inearlygaveup on 2009-02-28
> **taurus said:**
> If you want to resize your harddrive (expand to take up the unallocated space).........

Also, **it depends on where the unallocated space is located.**

```
sudo fdisk -lu
```

[I]Morning (UK Time 8:20am) and thanks again,I need to ask some more questions about the above... or would you prefer I start a new thread.
[/I]
**_There may be big gaps between any replies as I won't be online all the time this weekend _**

sudo fdisk -lu

output is


/dev/sda4       123090030   195366464    36138217+   f  W95 Ext'd (LBA)

/dev/sda5       156457098   159172019     1357461   82  Linux swap / Solaris

/dev/sda6       159172021   195362816    18095398   83  Linux

/dev/sda7       123090156   150352334    13631089+  83  Linux

/dev/sda8       154963053   156457034      746991   82  Linux swap / Solaris

/dev/sda9       150352398   154625624     2136613+  83  Linux

/dev/sda10      154625688   154962989      168651   82  Linux swap / Solaris



Partition table entries are not in disk order

martin@martin-laptop:~$

---

