---
title: "I am trying to install additional HDD to my Ubuntu 14.04.3"
date: 2017-03-29
forum: Hardware
---

### Post by hanana on 2017-03-29
Hi

I just re-install Ubuntu 14.04.3 to my desktop and ubuntu is exist on my sda1(SSD).

and i have an another 3TB HDD, but it contains huge amount of deep learning datas.(almost 1TB)

i'm trying to add 3TB HDD, but none of any google answers say "Add additional HDD to Ubuntu WITHOUT FORMATTING"

so could you please tell me how can i add 3TB HDD without Formatting???


i was tried it on Windows 10, it detects on Settings(HDD Partition dividing settings) but ALSO couldn't access without adding partition.

---

### Post by Bucky Ball on 2017-03-29
Sure. Plug it in and switch on your machine. :)

What makes you think you need to format or do anything else to it? It only needs power and a connection to your motherboard and that's it. Ubuntu is not going to format anything unless you tell it to, which I presume you're not going to do.

Depending on your setup, the drive, or rather the partitions on the drive, should pop up in your file manager like any other partition. You will not be asked to format them and the disk and its partitions certainly will not be formatted by Ubuntu when you switch your computer on. Why would it be?

Good luck. If you have any issues seeing the partitions on the drive once you've plugged it into your machine, let us know.

PS:

> **hanana said:**
> ... none of any google answers say "Add additional HDD to Ubuntu WITHOUT FORMATTING"

Probably because if you add a hard drive to a Ubuntu machine it won't format it, so non-question. You can already add a hard drive to your machine without formatting by default. The formatting part is up to you once the disk is in the machine and operational. Whatever is on the disk is not going anywhere until you say otherwise. :)

---

### Post by ajgreeny on 2017-03-29
Once you have aattached the disk to your machine show us the output of command ```
sudo parted -l
``` so we can see the partitions on the new disk and we can then tell you what to add to /etc/fstab to automount whatever partitions you need mounted at boot.

---

### Post by hanana on 2017-03-29
i solved it.

firstly, i removed automatically detected wrong partition(0.5KB)

fdisk /dev/sdb 
d #delete partition

and robooted.

sudo fdisk -l #for check its name - sdb

fdisk /dev/sdb
n #make a new partition
p #select as a primary partition
1 #numbering
Enter
Enter #for First sector and Last sector
p
w #for wirte and quit

mkdir /srv/data1 #for mounting directory
sudo mount /dev/sdb #for mount hdd

sudo blkid # for check HDD UUID
sudo vim /etc/fstab #for automatic mount
 UUID=UUIDaddress /srv/data1 ext4 defaults 0 0

sudo mount -a #for mount check
sudo chown -R username:username /srv #i don't know what is it :) PLZ tell me guys
sudo reboot

sudo mount /dev/sdb #for mounting checking


now my new HDD is connected to /srv/data1 folder
and access freely with my previous data!

---

### Post by Bashing-om on 2017-03-29
hanana; Sure !
(you do good work !)
> 
sudo chown -R username:username /srv #i don't know what is it &#65532; PLZ tell me guys

when the mountpont was created in the root environment (sudo)- then root owns the file system .
All you did here was to properly change that ownership ( R is Recursive for all lower level directories and files ) from that of root to "you" .  Such that "you" have access permissions to the respective file system .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

