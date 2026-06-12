---
title: "usb drive/sd"
date: 2016-11-05
forum: Hardware
---

### Post by jgw on 2016-11-05
I have a usb drive which I cannot change some permissions on.  I can change the owner stuff, I can remove the entire partition, create a new partition, and format.  I have given it a 32 bit partition and formatted it to 32 bit (and several other options - none of which changed anything).  My problem is that, other than the owner, the permissions are "access files" and that's it.  If I left click, and try and change permissions that way it pretends to change it to "create and change" but switches it back to access files immediately.  I have tried several combinations of partition and format - to no avail.  

I have several of these usb drives and they are all screwed up.  What I am trying to do is to empty everything off them and re-do them.

Thank you ....................

---

### Post by sudodus on 2016-11-06
Microsoft file systems, FAT32 and NTFS, will get the ownership and permissions when mounted in linux, while linux file systems, for example ext4, can be managed with ***chown*** and ***chmod*** on the directory and individual file level.

So you solve (maybe it's better to say work around) the problem in two ways.

***1. Use a linux file system, for example ext4.***

***2. Use a Microsoft file system, and make sure to mount it with suitable permissions.***

Mount a FAT32 partition in a pendrive with read/write permissions for everybody:

(assumption: the pendrive is seen as /dev/sdx, replace x with the actual drive
letter, for example b: /dev/sdx1 ---> /dev/sdb1)

```
sudo mkdir -p /mnt/sd1  # only if you want a new mountpoint
sudo umount /dev/sdx1   # only if already mounted (but with bad permissions)

sudo mount -o rw,users,umask=000 /dev/sdx1 /mnt/sd1  # mount

echo 'Hello World' > /mnt/sd1/hello.txt  # test writing
cat /mnt/sd1/hello.txt                   # test reading
```

-o-

You can re-do USB drives with mkusb - the wipe menu:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by jgw on 2016-11-07
Thank you for the reply.

Let me try and say what I think is going on here.

First - the fat file filesystem (ntsb, 32 bit, etc -windows stuff) will work with everything.  However, windows has no idea about ownership, and permissions, so, basically, when in windows one can pretty much do what they want but, in linux, one must have not only owner, users, whoever but those items must have the proper permissions to function properly.  These permissions cannot really be set on the fat filesystem as it doesn't have such.  One can, however, take a fat filesystem usb drive and mount it so that one can control owner, user, and permissions.  This mounting, however, will apply to the specific usb drive and does not travel with the usb drive itself?

I have deleted all partitions on a usb drive and then installed the ext4 partition as the main one.  I then formatted said partition as a fat file system.  Unable to change permissions unless specifically mounted with "sudo mount -o rw,users,umask=000 /dev/sdx1 /mnt/sd1", for instance.  In that case one can deal with it in linux.  On the other hand, if one installs an ext4 partition AND file system one can, pretty much do whatever they want with owners, users, others and all the permissions.

Do I have it?

Thank you....................

---

### Post by sudodus on 2016-11-08
I think so.

-o-

Can you manage the ownership and permissions now, so that you can do what you want with your USB drives?

---

### Post by jgw on 2016-11-08
Yes - what I am going to do is to create two sets of sd things.  The first, windows, will have 'windows' in the sd name whilst those for linux will not.  Since most of what I do is on Linux (my wife's machine is the only windows machine) That will be quite easy.  I have spent a lot of time on this one and am glad to be shut of it.

Its too bad that ubuntu/linux doesn't catch windows usb sd's and, if somebody is trying to change something note what it is and a example of what needs to be done before such changes are possible.  Oh well..............

Thank you for all the replies!

---

