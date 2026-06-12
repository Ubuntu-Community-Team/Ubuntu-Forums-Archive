---
title: "Stop partitions being detected"
date: 2011-02-05
forum: Hardware
---

### Post by canoemoose on 2011-02-05
Hi all,
I have a machine running 10.10 with 2 hard drives; one contains /, /home and swap and the second has partitions mounted at ~/Videos, ~/Music and a Windows partition.
The second drive was installed after the machine had been in use for about a year.
I've added the Videos and Music partitions to my fstab, so they mount automatically at boot.

The partitions on the second drive are detected as separate "drives", and show up in Nautilus as separate devices.
I want them to behave as the separate home partition does, and be "invisible" from the user's point of view, to avoid cluttering Nautilus up, as the machine often has a large number of external drives mounted and one day someone is going to unmount the wrong device by accident.

Is this possible?

---

### Post by oldfred on 2011-02-05
Yes. there of course are several ways.

I mount partitions else where and link them back in.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I have all my folders (13 or 14) in one data partition.
sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

If you only have two partitions you can directly mount them with fstab.
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by canoemoose on 2011-02-05
Correct me if I'm wrong, but surely that won't prevent Nautilus from seeing the ~/Music and ~/Videos partitions as separate drives?

I want Nautilus to "forget" that they are on separate partitions, as it already does for /home.

This is already the default behaviour if the drive is installed when the OS is originally installed.

---

### Post by oldfred on 2011-02-05
Only if you mount directly into /home or /media do you see the partitions (There also is another workaround but I forgot). With my mount in /mnt, I do not see the partitons. In fact when I want to do a few things like backup or connect from my other computer the links do not work and I have to use the full paths.

---

