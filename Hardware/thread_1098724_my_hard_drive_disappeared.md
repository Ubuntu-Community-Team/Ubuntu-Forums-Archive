---
title: "my hard drive disappeared"
date: 2009-03-17
forum: Hardware
---

### Post by anili100 on 2009-03-17
I have just dual boot Ubuntu and Windows XP on my laptop. Before installing Ubuntu I had 320 GB hard drive divided in 3 parts C - 30 GB, D - 140 GB and E - 150 GB. After I installed it, I only have 3 GB on my drive E. How can I get my free space back? Please help me!

---

### Post by taurus on 2009-03-17
First thing first.  Did you install Ubuntu on it own partition or did you install Ubuntu from windows--wubi?

---

### Post by anili100 on 2009-03-17
I used the Live CD and went on full instalation. When i came to the partition step, I clicked guided and I went on. It took about half an hour to install it. I really don't know what's happening..

---

### Post by taurus on 2009-03-17
Open a terminal and post the outputs of these commands, running one line at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by anili100 on 2009-03-17
Here's the output:
sudo fdisk -l:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac047005

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38913   281852392+   f  W95 Ext'd (LBA)
/dev/sda5            3825       21034   138239293+   7  HPFS/NTFS
/dev/sda6           21035       21426     3148708+   7  HPFS/NTFS
/dev/sda7           21427       38198   134721058+  83  Linux
/dev/sda8           38199       38913     5743206   82  Linux swap / Solaris

sudo blkid:
/dev/sda1: UUID="CAA05AB0A05AA2AD" TYPE="ntfs" 
/dev/sda5: UUID="A0C46173C4614C9A" TYPE="ntfs" 
/dev/sda6: UUID="AC24668C246658FA" TYPE="ntfs" 
/dev/sda7: UUID="0b8599f2-91b6-4498-af4e-f610db2f2ff0" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="e4dab984-a0ba-4843-83d9-be17144131e0" 

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0b8599f2-91b6-4498-af4e-f610db2f2ff0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=e4dab984-a0ba-4843-83d9-be17144131e0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             127G  3.0G  118G   3% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  2.8M  1.4G   1% /dev
tmpfs                 1.4G  264K  1.4G   1% /dev/shm
lrm                   1.4G  2.0M  1.4G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6             3.1G   69M  3.0G   3% /media/disk
/dev/sda5             132G  2.0G  130G   2% /media/disk-1

---

### Post by taurus on 2009-03-17
So you are saying that you gave Ubuntu, /dev/sda7, too much space (~127GB) when you installed it.

---

### Post by anili100 on 2009-03-17
I don't know,but I don't have access to /dev/sda7. It looks like it's lost. It's not visible in XP either.

---

### Post by taurus on 2009-03-17
It is _definitely_ not lost.  /dev/sda7 is your root filesystem.  So if you run Ubuntu, you are using /dev/sda7.

```
**[COLOR="Blue"]/dev/sda7 127G 3.0G 118G 3% /[/COLOR]**
```

Windows cannot read or access ext2/ext3 unless you install a 3rd-party software to do so, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by anili100 on 2009-03-18
> **taurus said:**
> So you are saying that you gave Ubuntu, /dev/sda7, too much space (~127GB) when you installed it.
I guess I gave Ubuntu too much space... Any idea how to take the space back?
I tried to resize it using GParted, but it's locked.

---

### Post by taurus on 2009-03-18
Try using gparted from the LiveCD since you cannot resize a partition while you are running/using it.

---

### Post by anili100 on 2009-03-18
That worked great for me! Thanks a lot!

---

