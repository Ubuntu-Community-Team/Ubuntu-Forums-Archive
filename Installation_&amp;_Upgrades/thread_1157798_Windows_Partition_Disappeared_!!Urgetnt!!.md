---
title: "Windows Partition Disappeared !!Urgetnt!!"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by us3598 on 2009-05-13
Hey all, 'preciate some help here.
OK. Just upgraded xubuntu to 9.04 jaunty jackalope. Was able to see and interact with sda1 (windows FAT32 partition). Now it's gone, both from fstab and mtab...when I run sudo fdisk -l it shows up though. I'm baffled, and have some extremely mission critical files to xfer over from xubuntu. Any suggestions?

---

### Post by ndefontenay on 2009-05-13
Can you boot at all on windows?

---

### Post by us3598 on 2009-05-13
Yes, windows boots just fine...the partition just magically disappeared from xubuntu...it worked just fine last night.

---

### Post by Peter09 on 2009-05-13
What does

```
df -h
```

show

---

### Post by us3598 on 2009-05-13
pglenn@IT-Master:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             8.2G  3.9G  4.0G  50% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  348K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  144K  249M   1% /dev
tmpfs                 249M     0  249M   0% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by Peter09 on 2009-05-13
have you tried to mount sda1 ?
```

sudo mount -t vfat /dev/sda1 <an empty folder of your choice>
```

---

### Post by us3598 on 2009-05-13
tells me special device sda1 does not exist

---

### Post by Peter09 on 2009-05-13
You will need to create the folder first - note my command contained an error - just look again.

---

### Post by us3598 on 2009-05-13
same message, special device /sda1 does not exist.

---

### Post by Peter09 on 2009-05-13
did you use /dev/sda1 ?

---

### Post by us3598 on 2009-05-13
ok, sda1 is in the /dev folder, not in the fstab, but shows up on fdisk. created /media/sda1, but it's empty, and I cant mount it because it "does not exist"....hmm....this is wierd. Especially since between last night and tonight I have changed nothing, and it worked flawlessly then.

---

### Post by us3598 on 2009-05-13
sure did

---

### Post by saivin on 2009-05-13
Hi,
Try the following:
```

sudo mkdir /tmp/windoz
sudo mount -t vfat /dev/sda1 /tmp/windoz

```
if it shows some fault,
```
dmesg | tail
```
Let us know the error.

Btw, is your /dev/sda1 really FAT32?  Coz, usually windows prefers NTFS partitioning. Whats the output of ```
fdisk -l
```
Just try,```
sudo mount -t ntfs-3g /dev/sda1 /tmp/windoz
```

---

### Post by Peter09 on 2009-05-13
Can you show me the output of fdisk?

---

### Post by us3598 on 2009-05-13
hmmph, mounting to tmp/windows solved it....that's wierd. Why wouldn't it mount normally?

---

### Post by us3598 on 2009-05-13
and btw...thanks a crapton guys...I REALLY appreciate it...I would've really been in the gutter if I couldn't get these files xferd over..you are true lifesavers. I endeavor to procure your level of linux knowlege.

---

