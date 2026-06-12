---
title: "New Hard Drive Install Questions"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by s|k on 2006-11-26
Hi,

I am about to install a brand new 250GB ULTRA ATA/IDE hard drive onto my ubuntu-server box that has about 180mb or ram and was made for windows 98. It's a total command line interface and I was wondering if there is anything I should know in advance (probably should have asked before buying) and specfically, once I add the hard drive, how do I access it and create and move directories to it? How does one 'map' a drive on Ubuntu-server via CLI.

Thanks.

---

### Post by procras on 2006-11-26
There were some problems with huge hard drives on old boards, you may want to google
your mainboard and harddrive.

If the drive works it is easy to use it with Linux. You do not need the gui at all.
Old fashioned way.

- Plug in your harddrive
- Boot machine and look at dmesg to see if anything nice pops up.

- You are putting it into an old machine then that will only have an IDE interface on the board. 
- Main drive is /dev/hda
- New drive is /dev/hdb

You need to enter these commands as root, in a root shell or with sudo

- Use fdisk to look at partitions and types on /dev/hdb
$ fdisk /dev/hdb
Make your partitions eg hdb1 type ext2 or what you want
Do not forget to write the partition info to the disk!

- Use e2fstools to create the partion you want to access
$ mke2fs /dev/hdb1

- Create a mount point on your main drive any empty dir will do
$ mkdir /driveb

- Mount your new drive
$ mount -t ext2 /dev/hdb1 /driveb

- You can make this happen at boot by editing /etc/fstab and entering 
an appropriate line there

- Use your new drive eg backup your files or what ever you want.
$ rsync -avz /home/youname/ /driveb

---

