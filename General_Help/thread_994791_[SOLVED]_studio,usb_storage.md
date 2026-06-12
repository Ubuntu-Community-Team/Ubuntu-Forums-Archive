---
title: "[SOLVED] studio,usb storage?"
date: 2008-11-27
forum: General Help
---

### Post by rixtr66 on 2008-11-27
I started out with ubuntu,then moved it to an external hard drive to try
different distros.after running slackware,zenwalk,gentoo,open suse,elive,
and a couple others,i decided to come back to ubuntu.so now im using 
ubuntu studio as it suits me pefectly.anyway studio is my sole os now
and i want to use my usb harddrive as storage,but i dont know how to set it
up that way? its a wd 250g usb drive.i have no problems setting up os's
on it but i dont know how to format it and have it be an extension of my
internal hd.could someone help me with this?:confused::confused:
much appreciation!
peace.
Rick

---

### Post by rixtr66 on 2008-11-28
Hello.................Is this thing on?
heh heh,sorry just having some fun.
could really use some help though!!
please.
no seriously.
thanks
Rick:(

---

### Post by taurus on 2008-11-28
If there is nothing valuable on that drive, use gparted to format it to ext3.  Then, edit /etc/fstab and add an entry for that harddrive so it would be mounted automatically each time you boot.  And if you want to write to it without using sudo/gksudo, then you need change the ownership of the mountpoint of that harddrive from root to your login name.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by rixtr66 on 2008-11-28
Thank you for answering my post!!
here is the output you asked for;

```
rick@ubuntu:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29648   238147528+  83  Linux
/dev/sdb2           29649       30401     6048472+   5  Extended
/dev/sdb5           29649       30401     6048441   82  Linux swap / Solaris
rick@ubuntu:~$ 
```
the linux version on there is ubuntu 8.04 wich i was using while exploring
other linux distros,but since im using ubuntu as my sole os i can delete
this.i know how to use gparted,but since my brain injury,im kinda foggy
on how to write it to /etc/fstab.so a little help there would be nice.
thanks!!! Rick

---

### Post by taurus on 2008-11-28
Looks like /dev/sdb1 is the one you want to mount.

Edit /etc/fstab and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it. Now, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by rixtr66 on 2008-11-28
Excellent!!Thank you.give me some time to muddle through this,and i'll 
let you know ho it works.
thanks again!!
peace
Rick

---

### Post by taurus on 2008-11-28
And if you want to write to /media/sdb1, then you need to change the ownership of /media/sdb1 from root to your login name, rick.

```
sudo chown -R rick:rick /media/sdb1
ls -la /media
```

---

### Post by rixtr66 on 2008-11-28
Well it looks like every thing went well.
i got an output on the last command;

```
rick@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  8.7G   59G  13% /
varrun               1003M  120K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   56K 1003M   1% /dev
devshm               1003M   48K 1003M   1% /dev/shm
lrm                  1003M   40M  964M   4% /lib/modules/2.6.24-22-rt/volatile
/dev/sdb1             232G  188M  220G   1% /media/sdb1
rick@ubuntu:~$ 
```

does this mean everything is working?
another question if you dont mind.
im assuming this will be mounted at startup.
since ive never used this drive for storage,is access to this drive like
acces to my internal hd?or is it just an extention,like a usb pen drive?
maybe im not asking the right question!im a little confused at the moment
sorry!i think im  a little unsure of how to use this drive.
damn!!i used to be so good at this.well thanks alot!!!
you have been very helpfull!!
Rick

---

### Post by taurus on 2008-11-28
You can either access that drive/partition from a terminal or with nautilus.  Remember, it is /media/sdb1.

```
ls -la /media/sdb1
```

---

### Post by rixtr66 on 2008-11-28
Well allllrighty then :) Thanks!!i think i will find this most usefull.
ive written everything down so i will remember!!eventually it will sink in.
you are the master of the ubuntu groove!! :guitar:
thanks a bunch!!
Rick:)

---

