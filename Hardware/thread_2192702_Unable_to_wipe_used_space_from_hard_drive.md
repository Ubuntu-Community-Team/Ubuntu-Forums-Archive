---
title: "Unable to wipe used space from hard drive"
date: 2013-12-09
forum: Hardware
---

### Post by ryansmailinglist on 2013-12-09
I recently converted from Windows 8 to Ubuntu 13.10.  I have a 120 GiB solid state drive (sda) and a 2 TiB standard hard drive (sdb).  I have root, SWAP, and /home on the solid state drive.  I used the following to wipe my large second hard drive in preparation for partitioning and mounting it for storing data files:

sudo dd if=/dev/sdb/zero or=/dev/sdb bs=30M

The process completed and said it had wiped the entire 2 TiB, but when I use GParted, the device shows a size of 1.82 TiB, with 29.42 GiB used, and 1.79 TiB free.  I would like to know how to reclaim the ~30 GiB so I can use my whole hard drive.  My Windows 8 OS was on my solid state drive and was removed prior to running the wipe operation.

---

### Post by drmrgd on 2013-12-09
The only way that I've ever done something like this was to wipe the partition table with parted and rebuild it the way I want. Depending on what you've got, that extra 30GB might be some kind of hidden system partition that dd didn't mess with.  I think the following may work (I usually follow this as I'm not in the habit of buying large drives and formatting them all GPT :) ):

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Hope that helps!

---

### Post by ryansmailinglist on 2013-12-09
Thanks, I tried it out, but when using the command:

> mklable gpt

I returned the error
> partition 1 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

Any advice?

---

### Post by ryansmailinglist on 2013-12-09
Some more information, it appears that this drive is somehow permanently mounted to /media.  Perhaps the 30 GiB of information on the drive somehow got attached to that location such that it cannot be freed.

> ryan@ryan-System-Product-Name:~$ sudo umount -vfd /dev/sdb1
/dev/sdb1 has been unmounted
ryan@ryan-System-Product-Name:~$ sudo mount /dev/sdb1 /mnt/data
ryan@ryan-System-Product-Name:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G  4.6G   14G  25% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            4.2G   13k  4.2G   1% /dev
tmpfs           832M  1.3M  831M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            4.2G  152k  4.2G   1% /run/shm
none            105M   74k  105M   1% /run/user
/dev/sda6        67G  782M   63G   2% /home
/dev/sdb1       2.0T   71M  1.9T   1% /media/ryan/My Files
/dev/sdb1       2.0T   71M  1.9T   1% /mnt/data

---

### Post by ryansmailinglist on 2013-12-10
Another update:

You were correct about changing the partitioning table.  The previous data must have been a relic.  In order to change the drive to a GPT, I had to boot off of the USB image file.  I actually booted from the USB, used GNU parted to set both hard drives to GPT, then reinstalled Ubuntu, then partitioned the 2 TiB drive as ext4 and mounted it to /mnt/data.  Worked great, a lot of work, but it turned out!  Thanks for the help!

---

### Post by drmrgd on 2013-12-10
Great!  Glad that worked out.  Sorry was offline for most of the night last night, but seems you're good to go now.

---

### Post by codenine75a on 2013-12-10
I love dd.  I used it to wipe a mbr virus from a windows machine.  DD is also good for computer forenesics and hard drive imaging.

---

