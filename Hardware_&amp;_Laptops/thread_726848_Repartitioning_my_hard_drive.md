---
title: "Repartitioning my hard drive"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by haraldmilz on 2008-03-17
Hi,

I have a 160GB HDD which I originally partitioned 50% for Ubuntu and 50% for windows. I now used gnome partition editor to convert that second windows partition to an ext3 partition. As I didn't know how to join both partitions, i mounted the remaining 50% of my HDD on some folder where I run my Virtual Machines (I really need those to keep on running!!).

Now here is my request for help: I can't seem to find a way to "join" both partitions to "/" so that I have only one partition and not a second 50% partition mounted on a folder I am not even sure I will use to it's 100%.

Thank you!

---

### Post by blueturtl on 2008-03-17
Are you using LVM?

I understand that LVM was created solve spesifically this types of problems. I think Ubuntu even by default sets up LVM if you don't meddle with partitioning during the install process..

---

### Post by haraldmilz on 2008-03-17
Logical Volume Manager. I know what it means but I don't know how it works nor if I have it implemented. I thought the gnome partition editor screenshot would help you out. Please help me understand if I am using LVM. Thank you!

---

### Post by haraldmilz on 2008-03-17
I just found out what LVM is:
LVM supports enterprise level volume management of disk and disk subsystems by grouping arbitrary disks into volume groups. The total capacity of volume groups can be allocated to logical volumes, which are accessed as regular block devices

... and it is not the solution I am looking for. I Have the following problem:

I have partitions A > B > C. Partitions A and C are ext3. Partition B is SWAP.. I want to know if there is a tool to change my partitioning so that I have my HDD with the following partitioning:

A ext3 (which is A and B JOINED, not grouped)
B Swap at the end of the hard drive and not at the middle like it is now.

I am about to reinstall Ubuntu just because of the partitioning. I have everything setup on my actual Ubuntu... maybe someone could save me several hours of work? Thank you!

---

### Post by sandysandy on 2008-03-17
had a look.

u may consider following

delete sda 5 (SWAP)

shift sda3 to left

create SWAP on extreme right in free space

here is a link to tutorial on gparted.

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Backup important data as safety prior to resizing.


regards

---

### Post by haraldmilz on 2008-03-17
Thank you Sandy for your answer. I will check on the guide,

---

### Post by bigredradio on 2008-03-18
Why would you want to combine them? If anything you should break them up more. I would actually use LVM on the 2nd parition so that you can break it up into multiple filesystems. This is linux, not windows folks. Having multiple filesystems is a good thing. Lumping everything together slows performance, greater chance of catastrophic failure and less flexibility.

LVM is a nice way to flexibly break up the system. Partitions are pretty fixed once you are done. (as you are finding out). If you use LVM you can grow, shrink, create, delete the devices that the filesystem is created on. But, you might want to first consider why you want to combine them.

---

### Post by haraldmilz on 2008-03-19
> **bigredradio said:**
> Why would you want to combine them? If anything you should break them up more. I would actually use LVM on the 2nd parition so that you can break it up into multiple filesystems. This is linux, not windows folks. Having multiple filesystems is a good thing. Lumping everything together slows performance, greater chance of catastrophic failure and less flexibility.

LVM is a nice way to flexibly break up the system. Partitions are pretty fixed once you are done. (as you are finding out). If you use LVM you can grow, shrink, create, delete the devices that the filesystem is created on. But, you might want to first consider why you want to combine them.

--------------------------

Thanks blueturtl and bigredradio, LVM was finaly the closest solution to my problem. 

Greetings,

Harald

---

