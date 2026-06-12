---
title: "kded  eats 99% CPU when inserting disc"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by wazyk on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/16491](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/16491) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
I have this bugging problem since Edgy (thought it would be resolved with an upgrade to Feisty but not) : when I insert a CD-Rom or DVD, I i'm stuck on this screen :
[IMG]http://img230.imageshack.us/my.php?image=capturecdma5.png[/IMG]
The disk as about to mount and kded goes eating 99% of CPU.
If I restart X with the disk still in, it restarts OK, with the disk mounted as normal...

It looks like :  [http://lists.kde.org/?l=kde-devel&m=110719156320385&w=2]("http://lists.kde.org/?l=kde-devel&m=110719156320385&w=2")
or
this old bug : [https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/16491]("https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/16491")

I'm on DELL Inspiron 6000 (Breezy > Dapper > Edgy > Feisty)

I don't think it has anything to do with the fstab but here it is :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5 -- converted during upgrade to edgy
UUID=F9E3-0380 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=f66cc591-37c1-40a6-a23e-c44c9e0e44f5 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-0110 /media/sda1 vfat defaults,loop,uid=0,gid=0,noauto,ro,nouser 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=C2A89796A8978795 /media/sda2 ntfs defaults,loop,uid=0,gid=0,noauto,ro,nouser 0 0
/dev/sda3 /media/sda3 vfat defaults,uid=0,gid=0,auto,rw,nouser 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=53c35d45-9e7c-4e53-8bbc-79a043f17b7c none swap sw 0 0
# cdrom/dvd
#/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
# /dev/sda9 -- converted during upgrade to edgy
UUID=BC805BAB805B6B42 /home/eric/Documents ntfs defaults,uid=1000,gid=100,auto,ro,users 0 0
# /dev/sda8 -- converted during upgrade to edgy
UUID=2ac7093a-9e4a-418c-b16b-7d473d2e7c34 /home/eric/Media ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 0
# isos
/home/eric/Media/Jeux/iso/adiboudchou.iso /mnt/iso/drive_1 iso9660 ro,loop,auto 0 0
```

Any help ?

Thanks

---

### Post by wazyk on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/109876](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/109876) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Up ?

I've attached a launchpad report

---

