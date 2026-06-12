---
title: "Create a 'Fake' RAID 1 Partition"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by bones349 on 2009-07-15
Hello.
I need to create a partition on a separate drive (this drive is only for data, not booting), using RAID 1.
I've learned that my RAID controller is 'fake' (ASUS Rampage II Extreme).  It works fine in Vista (with drivers), but now I'd like to setup a partition in Kubuntu.
gparted displays the drives as two separate 1 TB drives.
I've read this tutorial:
[https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.04%20(Jaunty%20Jackalope]("https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.04%20%28Jaunty%20Jackalope"))
but found it very confusing.  Im NOT booting from this drive, just want to create a giant EXT3 partition.
Any ideas?
I have gparted, dmraid installed already.
Thanks

---

### Post by ronparent on 2009-07-15
To get ubuntu to see the two drives as a single the raid1 array, you need to install dmraid. This is a program that serves the same purpose as the raid driver for your mb raid hardware in windows. After you do this you will see your array including its partitions in gparted. At that point you will be able to create a new raid partition or resize or delete any existing partition of any type using gparted. Note that the separate drives will still appear in gparted and you shouldn't use gparted to act on any individual component drive of the raid array. That will destroy the integrity of the array and make your life much more complicated, especially if you still need access to the array with windows. 

To install dmraid, open a terminal and enter **sudo apt-get install dmraid -y**. Most of the time this will also activate the array (write the symbolic links in /dev/mapper you need to mount any array partition to your file system). To be certain however enter **sudo dmraid -ay** to activate the raid partition(s). The easiest way to access any raid partition is to create a mounting instruction in /etc/fstab to mount it to a location you have to manually create in your file system for that purpose. This will take the form -

/dev/mapper/<sysmbolic link name> /media/<the folder name you create> etc

Use only the symbolic link names with a number (the one without a number represents the entire array which has no file system per se and is not mountable). You can create the folder you want the partition mounted to anywhere in the file system (ie in /media, /mnt, /name_you_create, etc). If you get hung up anywhere, post here and someone will try to help you.

---

