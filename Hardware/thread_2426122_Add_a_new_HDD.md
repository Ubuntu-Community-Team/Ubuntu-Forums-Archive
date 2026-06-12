---
title: "Add a new HDD"
date: 2019-09-04
forum: Hardware
---

### Post by saywot on 2019-09-04
I haven't used the optical drive of my Ubuntu 19.04 computer for, hmm, about as long as Disco Dingo has been released.
I have an HDD from a Fedora 30 computer sitting here doing nothing
How hard is it to unplug the SATA from the DVD drive, pop it over to the HDD then connect this drive to the power supply ?
I suspect it's pretty easy but I might get lost with the formatting then somehow expanding /home across the newly available 1TB.
I'd appreciate any hints/tips because I *really* don't want to do a full re-install.

---

### Post by cruzer001 on 2019-09-04
You need to purchase the cage that will fit in your model of laptop and hold the smaller ssd/hdd.  Examples

[https://www.ebay.com/sch/i.html?_nkw=laptop%20dvd%2Fssd%20cage&ssPageName=GSTL](https://www.ebay.com/sch/i.html?_nkw=laptop%20dvd%2Fssd%20cage&ssPageName=GSTL)

---

### Post by saywot on 2019-09-05
It's not a portable computer, the HDD is a 3.5" drive that will sit quite nicely on a spare 'shelf' in the case.

---

### Post by him610 on 2019-09-05
> HDD is a 3.5" drive that will sit quite nicely on a spare 'shelf' in the case
Make sure you secure it. You don't want it to be a able to rattle around inside of your computer.

---

### Post by TheFu on 2019-09-05
You probably don't want to "expand" the HOME onto the new disk.  While it is possible to merge a single file system across multiple disks through LVM, this is an excellent way to have complete data loss when 1 of the disks fails.  

However, you can add the other disk, partition it smartly, possibly use LVM (for future flexibility), either completely move the /home/ over to the new partition OR just mount the new partition somewhere out of the way and use symbolic links into it for large media and program files.

To know what makes the most sense, we need some data gathered - facts.

Connect up all the disks you want and run a few commands:
```
lsblk -e 7
sudo fdisk -l
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Please, post the command and the output together wrapped in "code tags", so things line up and look like it does in a terminal. If you don't, it is too hard to read correctly.
[https://www.howtogeek.com/426199/how-to-list-your-computers-devices-from-the-linux-terminal/](https://www.howtogeek.com/426199/how-to-list-your-computers-devices-from-the-linux-terminal/) explains some things that might help or not.

Facts are helpful. Thanks.

---

