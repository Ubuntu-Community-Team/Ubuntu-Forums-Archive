---
title: "problems after duplicating disk"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by balak on 2009-02-12
I was running out of space on my destop (with 160Gb hard drive) so I decided to upgrade to a 500Gb drive. I wanted to keep all my custom program/installations (I have been using ubuntu from breezy and upgrading every few months) and not have to reinstall ubuntu. So I decided to create new partitions on the new hard drive and copy the data from the old hard drive using 'dd'

For every partition, I did 
dd if=/dev/sda1 of=/dev/sdb1 and so on.
(sda - old drive, sdb - new drive)

However, the new partitions I had created were much bigger than the original partitions. For ex. sda2 (the root partition) was 10GB, while sdb2 was 20GB.

The duplication/transfer went off fine and I am currently using the new hard drive. However, when I check the remaining space on the partition using 'df' I get the same data as the old drive. gparted shows the right size for partitions but the "used" column looks bogus to me.

I have attached a snapshot of gparted, df (terminal on the left), fdisk -l (terminal on the right). 

Is there a simple way I can get back the space ? My root partition is running out of space and I would like to install some stuff in it. I tried copying a big file to /tmp (which comes under the root partition) but it errorred out with "no space left on device"

Thanks!

---

### Post by balak on 2009-02-12
Actually attaching the snapshot

---

### Post by blackgr on 2009-02-12
> **balak said:**
> I was running out of space on my destop (with 160Gb hard drive) so I decided to upgrade to a 500Gb drive. I wanted to keep all my custom program/installations (I have been using ubuntu from breezy and upgrading every few months) and not have to reinstall ubuntu. So I decided to create new partitions on the new hard drive and copy the data from the old hard drive using 'dd'

For every partition, I did 
dd if=/dev/sda1 of=/dev/sdb1 and so on.
(sda - old drive, sdb - new drive)

However, the new partitions I had created were much bigger than the original partitions. For ex. sda2 (the root partition) was 10GB, while sdb2 was 20GB.

The duplication/transfer went off fine and I am currently using the new hard drive. However, when I check the remaining space on the partition using 'df' I get the same data as the old drive. gparted shows the right size for partitions but the "used" column looks bogus to me.

I have attached a snapshot of gparted, df (terminal on the left), fdisk -l (terminal on the right). 

Is there a simple way I can get back the space ? My root partition is running out of space and I would like to install some stuff in it. I tried copying a big file to /tmp (which comes under the root partition) but it errorred out with "no space left on device"

Thanks!

Wrong wrong wrong. You do it all wrong. wipe your 500GB disk and do it again. Boot from a rescue cd or ubuntu live cd. Then do this

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

You dont have to create the partitions manually. This command will copy the complete 160GB disk with all its partitions and partition table to the new drive.

---

### Post by balak on 2009-02-12
> **blackgr said:**
> Wrong wrong wrong. You do it all wrong. wipe your 500GB disk and do it again. Boot from a rescue cd or ubuntu live cd. Then do this

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

You dont have to create the partitions manually. This command will copy the complete 160GB disk with all its partitions and partition table to the new drive.

Thanks for replying!

But I really don't want to have exactly the same partitions. I wanted to grow my /, /home, /music and /data partitions when I changed to the new disk.

---

### Post by blackgr on 2009-02-13
> **balak said:**
> Thanks for replying!

But I really don't want to have exactly the same partitions. I wanted to grow my /, /home, /music and /data partitions when I changed to the new disk.

JUst do this and after your system is working to your new drive you can resize partitions from a live cd with gparted

---

### Post by caljohnsmith on 2009-02-13
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo umount /dev/sda1
sudo e2fsck -f /dev/sda1
sudo resize2fs /dev/sda1
```
And repeat that for all your new partitions. Then boot back into your Ubuntu install, and please post the output of:
```
df -h
```
We can work from there if you want.

---

### Post by balak on 2009-02-14
caljohnsmith - you are the man! e2fsck and resize2fs did the trick.
Now I have the correct sizes for each of my partitions.

Here is the output of 
```

$df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  9.3G  9.7G  49% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  212K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  1.9G   1% /dev
tmpfs                 2.0G   44K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              99G   45G   50G  48% /home
/dev/sda7              99G  188M   94G   1% /music
/dev/sda8             197G   63G  125G  34% /data
/dev/sdb1             459G  164G  273G  38% /backup

```

---

### Post by caljohnsmith on 2009-02-14
Great, glad to hear that worked OK. I learned that trick from forum member meierfra, so you can give him credit for it. Cheers and enjoy your Ubuntu install. :)

---

