---
title: "Ext3 filesystem on Eee-pc harmful?"
date: 2009-01-23
forum: Hardware
---

### Post by Aat on 2009-01-23
Hi all,

I've read in some posts that putting a ext3-filesystem on an eee-pc with SSD-drive can be harmful. It is suggested to put ext2 on it instead.
Does a SSD-drive with a journaling filesystem wear out faster? If so, how much faster are we talking about? Should I really be worried about the life-expectancy for my lovely eeepc? Btw, i'm running 8.10 on a eee-pc 901.

---

### Post by jcoppala on 2009-01-23
I have an e3pc 8g... I use ubuntu 8.10 with ext3 with some hacks ...

I mount ext3 like it was ext2 
UUID=57480a3f-e7db-4a5e-9fca-7df45f5a7d9d /               ext2    defaults,noatime,errors=remount-ro 0       1

I have 2gb ram so I use tmp file system hack
tmpfs      /var/log        tmpfs        defaults           0    0
tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0
tmpfs      /var/log/apt    tmpfs        defaults           0    0

and the not swap
vm.swappiness=0 or vm.swappiness=1

Use the “noop” I/O scheduler
add "elevator=noop" as an option # defoptions=elevator=noop quiet splash

DISABLE SCROLLKEEPER: slow SSD it takes ages every time you install anything.

sudo mv /usr/bin/scrollkeeper-update /usr/bin/scrollkeeper-update.real
sudo ln -s /bin/true /usr/bin/scrollkeeper-update
sudo find /var/lib/scrollkeeper/ -name \*.xml -type f -exec rm -f '{}' \;
sudo dpkg-divert --local --divert /usr/bin/scrollkeeper-update.real --add /usr/bin/scrollkeeper-update

Asus has come out and said that the use of Journaled filesystems do NOT void the warranty
anyway it will take like 20 years for the ssd to die bye then U will get a new machine I hope so.
good luck
my eeepc never crushes... with this hacks... 

P.S.
google is your friend :)

---

### Post by Aat on 2009-01-23
so you are saying that the journaling doesn't harm the SSD?
In that case, are all those tweaks really necessary?
should I mount my / partition as ext2?

---

### Post by stchman on 2009-01-23
> **Aat said:**
> Hi all,

I've read in some posts that putting a ext3-filesystem on an eee-pc with SSD-drive can be harmful. It is suggested to put ext2 on it instead.
Does a SSD-drive with a journaling filesystem wear out faster? If so, how much faster are we talking about? Should I really be worried about the life-expectancy for my lovely eeepc? Btw, i'm running 8.10 on a eee-pc 901.

Basically with the EEEPC you will need to deactivate the swap.  The constant writing can cause damage as SSDs have a limited number of writes.

---

### Post by Aat on 2009-01-24
Well, I installed ubuntu without a swap partition, thinking 1GB RAM is enough for the OS to operate without problems. And I've had no problems so far.

Is that the same as deactivating swap?

---

### Post by AlexBellisBrown on 2009-01-24
Out of interest, what about ext4 on SSD? Because in future most linux distros will probably use that.

---

### Post by Aat on 2009-01-24
if journaling isn't the issue, i'm guessing ext4 will work as well.

still, i'd like to know if not having a swap-partition is the same as having swap disabled. or is there still a swap-file i have to disable?

---

