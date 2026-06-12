---
title: "HWE and ubuntu 12.04 server OMG :("
date: 2014-07-25
forum: Hardware
---

### Post by demanl on 2014-07-25
Hello,

I have a little server that has 3 hard drives in it and my world was GOOD.

sda               internal hard disk1              boot drive
sdb               internal hard disk2              data drive =========> contains all of my samba file shares
sdc               external usb disk1               backup data drive

And I had all the drives configured to mount at boot time using the /etc/fstab config file.


I then ssh into the machine and see the HWE only good to 08/17/2014 message with instructions on  how to upgrade to a newer supported version of the HWE......so I went ahead and followed those instructions and ran the supplied "apt-get install" command which ran thru to completion with no  problems at all.

So far so good.

About an hour later I reboot my little server and all seems well.

But...soon people are running around me screaming that they no longer can access any of their samba shares in windows.   So I quickly investigate and find that their claims are valid.....as I CANNOT FIND any of their DATA on the sdb drive at all.

I'M NOW IN FULL PANIC MODE...LIKE WTF did I do...?????

So I grab some coffee....add 10 spoonfull's of sugar...some cream....down it in 2 gulps....return to my little server and in my coffee-sugar induced state discover that my little server has recognized all of my three drives in a new and disturbing order.

sda  is now my external usb disk.
sdb is now hard disk1....which is still the boot drive.....
sdc is now hard disk2....where all of my data exists....quite okay by the way....just that samba was expecting all of my data to be on "sdb".

So I go into my /etc/fstab file and fiddle with my settings so that my mounts are matched to their now newly "NAMED" physical hard disks....reboot the server and all is WELL.

So....I had about 1-2 hours of "WTF did I do" moment today.

And I would now like to know what changed in the HWE that is now causing external usb drives to be placed "AHEAD"/"in front of" the internal physical disk drives...??

NOTE:  the internal physical drives are all sata drives.

I admit I am not a ubuntu/linux GURU....but I am learning...and evidently need to learn some more.

So please....all you ubuntu/linux GURU's please "TEACH ME".......what changed.....?

TYIA for any and all help with this....OH....please note my little server is still up and running........and running very well....:)

---

### Post by cariboo on 2014-07-26
I use UUIDs to mount my hard drives on my server, the entries in /etc/fstab look similar to this:

```
# /media/documents is on /dev/sdd1 
UUID=6f1f0afb-8cfe-4d7b-9ba9-15d42c37c4ab	/media/documents	xfs	defaults	0	0
```

To find the UUIDs of your drives, use:

```
sudo blkid
```

the result should look similar to this:

```
sudo blkid
[sudo] password for cariboo: 
/dev/sda1: UUID="e46578e3-2486-4fa1-b4d8-ca9e87883de0" TYPE="ext4" 
/dev/sda2: UUID="abeaa8a2-ab86-4011-8f31-94c8e443e6df" TYPE="swap" 
/dev/sda3: UUID="7ab93e78-6e78-4290-ae7e-5f87962b7c66" TYPE="ext4" 
/dev/sdc1: UUID="bc75bb38-6da9-4fb4-8061-1809479ce788" TYPE="xfs" 
/dev/sdd1: UUID="6f1f0afb-8cfe-4d7b-9ba9-15d42c37c4ab" TYPE="xfs" 
/dev/sde1: UUID="b573e178-54a1-4119-87b7-237555673cba" TYPE="xfs" 
/dev/sdb1: UUID="1fe87acc-57d8-4487-b919-ab39e2a673fd" TYPE="xfs" 
/dev/sdf1: UUID="1055075a-99e7-47ad-8cd9-dea0c98dd80a" TYPE="xfs" 
/dev/sdg1: UUID="b1debca6-d141-4d4a-b687-d410a2670cf7" TYPE="xfs" 
/dev/sdh1: UUID="151e1c53-0e1d-4c87-95d5-571c204138b6" TYPE="xfs" 
```

---

### Post by QIII on 2014-07-26
I give all the drives on my server a label -- usually from Norse legend -- and mount the drive by UUID with that name.  For instance /<some directory>/Thor or /<some directory>/Frigg.  If I tear the machine apart and get the drives plugged back in to different headers, oh well.  No problem.

I give the machines "tough guy" names like Duke or Zeek.

My family just needs to find the server by name on the network and map a drive on their Windows machines by the names: Ygdrassil, Thor, etc.

---

### Post by demanl on 2014-07-26
UUIDs for the WIN.....setting up all of my servers like this for now on.   Thankyou guys for the responses.

---

