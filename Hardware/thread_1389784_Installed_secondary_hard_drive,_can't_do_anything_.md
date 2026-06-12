---
title: "Installed secondary hard drive, can't do anything to it."
date: 2010-01-24
forum: Hardware
---

### Post by MrBaseball34 on 2010-01-24
I installed a second hard drive, created the partitions (ext3) and formatted it. However, I cannot do anything with the drive. I can mount it but I cannot copy any files there, create any files there, etc..

When I check permissions on the drive, it says that permissions cannot be determined.

What have I done wrong or need to do?

---

### Post by steveneddy on 2010-01-24
This states mounting Windows partition, but the directions are the same:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Windows_Compatibility](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Windows_Compatibility)

---

### Post by MrBaseball34 on 2010-01-25
Did exactly as shown but now can't even see it at all.
I do see the /storage virtual directory but it won't mount
as a drive.

---

### Post by Morbius1 on 2010-01-25
When in doubt go back to basics:

Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

---

### Post by warlockk on 2010-01-25
Try reformatting it . Might help because the thing with the permissions might be sorted out.

---

### Post by MrBaseball34 on 2010-01-25
> **Morbius1 said:**
> When in doubt go back to basics:

Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

```

sudo blkid -c /dev/null
********************************************************************
/dev/sda1: UUID="aa0dcef6-f17e-4008-b6d6-9b3fd4e5afaa" TYPE="ext3" 
/dev/sda5: UUID="F416-6C33" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="9d8a6102-d825-424e-b7ba-796f2ce590e3" 
/dev/sdb5: UUID="714af7d6-8cc2-4229-b4d5-83c36bfd29ec" TYPE="ext3" 

cat /etc/fstab
********************************************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa0dcef6-f17e-4008-b6d6-9b3fd4e5afaa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=F416-6C33  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=9d8a6102-d825-424e-b7ba-796f2ce590e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/sdb5
UUID=714af7d6-8cc2-4229-b4d5-83c36bfd29ec /storage ext3 defaults 0 0

mount
********************************************************************
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda5 on /windows type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb5 on /storage type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

---

### Post by Morbius1 on 2010-01-25
The partition in question is sdb5

From blkid:
> /dev/sdb5: UUID="714af7d6-8cc2-4229-b4d5-83c36bfd29ec" TYPE="ext3"From fstab:
> UUID=714af7d6-8cc2-4229-b4d5-83c36bfd29ec /storage ext3 defaults 0 0
from mount:
>  /dev/sdb5 on /storage type ext3 (rw)It looks to me that it's doing everything it should be doing. Of course fstab is going to mount it with root being the owner which means you as the user don't have access. To fix this:

Open **Terminal**
Type **sudo chown username /storage**

[COLOR=Blue][I]Change username above to your own login usernmae
[/I][/COLOR]This will change the ownership from root to you.

But the bigger problem is this:
> Did exactly as shown but now can't even see it at all.
I do see the /storage virtual directory but it won't mount
as a drive.     Is this still a problem?

---

### Post by MrBaseball34 on 2010-01-25
> **Morbius1 said:**
> <SNIP>
But the bigger problem is this:
Is this still a problem?

Yes, I still can't see it as a drive.

---

### Post by Morbius1 on 2010-01-25
I honestly don't know.

The mount command says its an ext3 partition that's been mounted to /storage which agrees with what you set up in fstab and agrees with what blkid says it is.

Now that you've done the chown you should be able to read and write to /storage.

You know it just occurred to me that you keep saying:
> I still can't see it as a drive.     Do you mean by that it's not showing up on the desktop or under "Places" in nautilus? It won't. Only mount points in /media or your /home directory will show up on the desktop.

But you should still have access if you go to /storage.

---

### Post by MrBaseball34 on 2010-01-26
> **Morbius1 said:**
> 
<SNIP>
Do you mean by that it's not showing up on the desktop or under "Places" in nautilus? It won't. Only mount points in /media or your /home directory will show up on the desktop.

But you should still have access if you go to /storage.

Exactly. Is there a way to "move" it to the /media or /mnt directory and make it show up without having to go through all that other stuff?

---

### Post by Morbius1 on 2010-01-26
Open **Terminal **
Type **sudo mkdir /media/storage**
Type **sudo umount /storage**
Type **gksu gedit /etc/fstab**

Change this:
> UUID=714af7d6-8cc2-4229-b4d5-83c36bfd29ec [COLOR=Blue]/storage[/COLOR] ext3 defaults 0 0                      To this:
> UUID=714af7d6-8cc2-4229-b4d5-83c36bfd29ec [COLOR=Blue]/media/storage[/COLOR] ext3 defaults 0 0                      Save the file and exit gedit. Back in the terminal:

Type **sudo mount -a**
Type [B]sudo chown your_username /media/storage

[/B]Unless I've made a typo somewhere you should be good to go.

---

