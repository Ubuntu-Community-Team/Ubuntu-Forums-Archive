---
title: "How do I mount at startup?"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by miceagol on 2007-01-12
I'm trying to mount a new partition, but when I do a reboot it's not mounted anymore. How do i mount it **each time** I load Ubuntu? Here's what I did:

1. Inserted the following into /etc/fstab
```

/dev/sdb2 ~/underholdning ext3 uid=1000,gid=1000,exec 0 0

```

2. Did
```

mkdir ~/underholdning

``` 

3. Mounted the drive
```

sudo mount -t ext3 /dev/sdb2 ~/underholdning

```

4. Did
```

mount -a

```

What am I forgetting? :confused:

---

### Post by Moldz on 2007-01-12
Try adding the auto option for that filesystem.  In your /etc/fstab file:
```
/dev/sdb2 ~/underholdning ext3 auto,uid=1000,gid=1000,exec 0 0
```

---

### Post by miceagol on 2007-01-12
> **Moldz said:**
> Try adding the auto option for that filesystem.  In your /etc/fstab file:
```
/dev/sdb2 ~/underholdning ext3 auto,uid=1000,gid=1000,exec 0 0
```

Didn't help. Still not automounted... :(

---

### Post by aysiu on 2007-01-12
Your system's broken, then.

Everything in your /etc/fstab is mounted at boot time.

Can you post your entire fstab? ```
cat /etc/fstab
```

---

### Post by finer recliner on 2007-01-12
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html)

read "making partitions automatically available

---

### Post by miceagol on 2007-01-12
> **aysiu said:**
> Your system's broken, then.


Harsh words... :shock:

> **aysiu said:**
> 
Everything in your /etc/fstab is mounted at boot time.

Can you post your entire fstab? ```
cat /etc/fstab
```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=41224d6c-4f65-455d-8396-a2903087cd27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=0ffe443c-4c05-42cc-b185-02e4a1daee15 /home           ext3    defaults        0       2
# /dev/sda2
UUID=DCC433D8C433B41C /media/vista    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=3A68F79868F750DD /media/xp       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=519c4c32-64e3-4cbe-ab25-fef1d2e2b614 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb2 ~/underholdning ext3 auto,uid=1000,gid=1000,exec 0 0
```

Fresh install btw.

---

### Post by aysiu on 2007-01-12
I could be talking out of my butt here, but is it possible that, for some strange reason, ~/ doesn't work as an /etc/fstab entry?

Have you tried using /home/miceagol/underholdning instead?

It may not make a difference, but it may be worth a shot, especially since ~/ usually stands for /home/currently-logged-in-user and there is no currently logged in user at boot time, except maybe root, in which case ~/underholdning would be /root/underholdning

---

### Post by miceagol on 2007-01-12
> **aysiu said:**
> I could be talking out of my butt here, but is it possible that, for some strange reason, ~/ doesn't work as an /etc/fstab entry?

Have you tried using /home/miceagol/underholdning instead?

It may not make a difference, but it may be worth a shot, especially since ~/ usually stands for /home/currently-logged-in-user and there is no currently logged in user at boot time, except maybe root, in which case ~/underholdning would be /root/underholdning

...or it might be me who thinks it's not mounted when it really is. :) GParted shows the correct mountpoint ~/underholdning for /dev/sdb2, though where I was looking was at df, which does not list /dev/sdb2 as mounted:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             41294832   2157164  37039984   6% /
varrun                 1037836        84   1037752   1% /var/run
varlock                1037836         0   1037836   0% /var/lock
procbususb               10240       192     10048   2% /proc/bus/usb
udev                     10240       192     10048   2% /dev
devshm                 1037836         0   1037836   0% /dev/shm
/dev/sda3            101241300    157916  95940600   1% /home
/dev/sda2            104857596  11702316  93155280  12% /media/vista
/dev/sda1            104857420  29858792  74998628  29% /media/xp

```
Is this the wrong place to look?

PS: I actually tried using /home/miceagol/underholdning first, but it didn't work at all (i.e. didn't even mount).

---

### Post by miceagol on 2007-01-12
Well, more info here. The mountpoint is greyed out in GParted. What does that mean? I tried copying some GB to ~/underholdning, but the change in free space occured on the partition where /home is mounted.

Is it just not possible to mount a partition in a subfolder of a folder which is mounted on a different partition? :-k

---

### Post by aysiu on 2007-01-12
My understanding is the whole point of mounting is that you can mount a partition to appear to be inside another partition.

You said mounting with /home/miceagol/underholdning didn't work? What happened exactly?

---

### Post by miceagol on 2007-01-12
> **aysiu said:**
> My understanding is the whole point of mounting is that you can mount a partition to appear to be inside another partition.

You said mounting with /home/miceagol/underholdning didn't work? What happened exactly?

I don't know what I did last time, but I managed to mount it that way now. Though, still same issues as with ~/underholdning. Greyed out in GParted, and does not show up in df after reboot. I'll try to mount it outside the /home-folder, and see what happens...

---

### Post by miceagol on 2007-01-12
Here's a little [screenshot]("http://folk.uio.no/michaeka/tilalle/Screenshot2.jpg") of GParted++. GParted happen to know which mountpoint I want, as I can select the partition and choose "mount on... -> /home/michaeka/underholdning". Starting GParted spits out the message:
```

======================
libparted : 1.7.1
automounting disabled
======================

```
Don't know if it means something though.

---

### Post by miceagol on 2007-01-14
Mounting outside of /home didn't work either. But I have an idea of a workaround: Creating a script I put into startup programs, which mounts the drive using:
```

mount -t ext3 /dev/sdb2 /home/michaeka/underholdning

``` 

One problem though. **Is it possible to make the script enter your password for sudo automatically, or is that a bit insecure?** :-|

---

### Post by aysiu on 2007-01-14
You can make a particular command not require a password. [Here's an example](http://ubuntuforums.org/showpost.php?p=123242&postcount=13).

---

### Post by miceagol on 2007-01-16
> **aysiu said:**
> You can make a particular command not require a password. [Here's an example](http://ubuntuforums.org/showpost.php?p=123242&postcount=13).

As explained in the link, I added
```

michaeka ALL = NOPASSWD: /bin/mount

```
to /etc/sudoers with visudo.

But I still need password to mount, even after reboot... :-|

---

### Post by miceagol on 2007-01-18
Sorry, just kidding. :oops: 

Just thought I didn't have to write sudo to do this, but when doing that I don't have to enter a password. Exactly what was supposed to happen. So now the drive mounts at startup after manually putting the mount command into startup programs in the sessions menu. :D Thanks a lot for your help!

---

