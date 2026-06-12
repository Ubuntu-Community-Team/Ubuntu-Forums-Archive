---
title: "Ubuntu confused by ntfs partition"
date: 2010-03-19
forum: Hardware
---

### Post by killachandra on 2010-03-19
I am using wubi to use karmic koala.
I have a 500 Gb single HDD partitioned as
C:\ = 100 GB Windows 7
D:\ = 300 GB Softwares, files, data
E:\ = 50 GB empty and i want to install ubuntu 9.10 here
F:\ = 15 GB Recovery partion created by dell when shipped.

Look at the pics below.
Ubuntu doesn't recognize D:\ and E:\ separately but as a single partition and unknown. Pls Help.

[[IMG]http://img151.imageshack.us/img151/7551/screenshotum.png[/IMG]](http://img151.imageshack.us/i/screenshotum.png/)

[[IMG]http://img405.imageshack.us/img405/5557/windows7p.gif[/IMG]](http://img405.imageshack.us/i/windows7p.gif/)



Now i want E:\ to install Ubuntu and remove the wubi installation. How do i make ubuntu to recognize D:\ and E:\ separately.

---

### Post by coffeecat on 2010-03-19
I have little experience of wubi-ised Ubuntu, but it could be that it is better to view your hard drive from outside of Wubi. Boot up from a live CD and go to Gparted there. What does it show? Post a screen shot.

By the way, posting huge linked images is discouraged here. Use 'Manage Attachments' under 'Additional Options' (below the text box) in the Reply to Thread page. You can upload your image and it is shown as a clickable thumbnail in the post.

**Edit:** by the way. The partition that is recognised by Windows as drive E: will be formatted NTFS. Do you realise that this will need to be reformatted to a Linux filesystem such as ext4? Also - you'll need a separate swap partition. Linux uses a swap partition, unlike Windows' swap file. Anyway - if Gparted from the live CD sees things better than from wubi, then I can tell you more after you've posted again.

---

### Post by killachandra on 2010-03-19
Bro i ran the live cd and the results the same as b4. by the way how can i format the 50 gigs in ext4 filesystem. also a little light on the swap partition wud be gr8. i am absolute newbie for ubuntu!!!

heres the link at gparted from livecd.
[http://img693.imageshack.us/img693/8125/screenshotgw.png](http://img693.imageshack.us/img693/8125/screenshotgw.png)

---

### Post by coffeecat on 2010-03-19
Don't do anything with that 350GB in Gparted. You will lose Data. Vista is seeing it as drives D: and E:, but Gparted can't make sense of it - I don't know why.

Before suggesting something, a quick word on partitions. As seen in Gparted, sda1, sda2 and sda3 are primary partitions. sda1 is your Dell utility, sda2 a 100MB partition that W7 likes for its own purposes and sda3 your Windows C: "drive". There is a maximum of 4 primary partitions per hard drive (with the partition table that you probably have). To get more, you have to create an extended partition (in place of one primary) which is merely a "container" for a number of logical partitions. This is what must be in that 350GB, but in a form that Gparted can't decipher.

The only solution that I can think of is to copy all the contents of D: to an external drive (to back it up) and then use Gparted to create an extended partition in the 350GB. (This will wipe the data in D: - hence the backup.) Then create three logical partitions: a new ntfs partition which Windows should see as D:, swap and ext4.

However, I suggest you do a bit more research before doing this. I don't understand why Gparted is not seeing how that 350GB is partitioned. Perhaps Dell has done clever things to the partition table. And if Dell has done something weird, you might run the risk of damaging the first three partitions if you let Gparted loose on it.

Sorry I can't be of more help. I suggest you see if someone comes along who has experience of the Dell way, or start a new thread in the Dell subforum:

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

### Post by killachandra on 2010-03-19
thanks for all the info bro. is it possible to format e:\ (50 Gb) into ext4 from windows 7 so i can chk if it makes a difference in gparted.

---

### Post by coffeecat on 2010-03-19
No. Windows knows nothing about Linux filesystems.

---

### Post by srs5694 on 2010-03-19
There is a port of the Linux ext2 filesystem to Windows; however, I don't know if that port includes a port of the mke2fs utility, which is used to create a filesystem ("format a disk," in Windows parlance). Even if it does, though, I don't think it would be wise to go down that path....

There are some types of partitions that hold other filesystems or partitions. Coffeecat has mentioned one: Extended partitions hold logical partitions. These are understood by both Linux and Windows. There are others, though, with less universal support. Linux has its own variety of logical volume management (LVM), for instance, in which filesystems are named and managed like files rather than the much less flexible partitions on which filesystems normally reside. An LVM can fill an entire disk, but more often its placed inside a partition. Windows has something similar, known as "volume sets," although I don't know much about it. My suspicion is that your Windows D: and E: drives are actually volumes in the Windows volume set scheme. To verify this, try typing "sudo fdisk -l" from a Linux command prompt. This will produce a list of the partitions as seen from Linux, including their type codes, as in:

```

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              64       38913   312062625   8e  Linux LVM
/dev/sda3              13          63      409657+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Note the "Id" column. Normal Windows NTFS partitions have a code of "7" in this column. Windows volume sets have numbers of 86 or 87, if the list provided by fdisk is to be believed. If that's what you see, then my hypothesis is almost certainly correct.

If I'm right, then my advice would be the same as what coffeecat suggested: Back up D: in Windows, delete /dev/sda4 in Linux, create a new extended partition in its place, create new NTFS and Linux logical partitions in the extended partition, restore D: to the new NTFS partition, and install Linux in its new partition(s). There may be a simpler way using Windows utilities that enable manipulation of its volume sets, though. Part of the problem is the 4-partition limit of the Master Boot Record (MBR) partitioning scheme that underlies all of this; since you've already got four primary partitions devoted to Windows, you *must* delete one of these or convert it to a logical partition inside an extended partition in order to gain the ability to create enough logical partitions for a Linux installation.

An alternative is to just buy a new hard disk and install Linux to it, leaving your current hard disk untouched. Even scavenging an old 40-80GB hard disk would give you roughly as much space as you were planning to devote to Linux on your current disk.

---

### Post by killachandra on 2010-03-20
thanks srs5694 for all the advice. Once again i am sorry but didnt quiet get how to create a swap partition and how much space to leave it and wat file system to format it with , now i plan to back up d:\ and merge d:\ and e:\ and create a partition with gparted in ubuntu

---

