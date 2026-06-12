---
title: "Hard drive formatting and avaliable space"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Oen386 on 2008-01-24
I have just formatted a 500 gig external USB drive. I have properly labelled the drive.

I have 2 problems.

First I have zero access on the drive, and have tried "sudo chmod -R 777 *" to make it so I can read/write etc... to it.

Secondly... Gparted is telling me (using Ext3) 7.5 gigs of the drive is in use... with nothing on it... but even worse Ubuntu (right clicking and clicking properties) tells me 23gigs are in use?!?

Can anyone clarify this for me? Thanks.

---

### Post by Oen386 on 2008-01-24
I guess it has to take up the 23 gigs... but I am still not sure why I see 2 different numbers from Gparted vs Ubuntu.

I still need help with the first question though.

I have tried "sudo chmod 777 /dev/sdb1" and "sudo chown username:group /dev/sdb1"

---

### Post by Oen386 on 2008-01-24
Weird.. finally got the chmod to work. Not sure what I did differently.

I am still curious why Ubuntu and Gparted show different sizes of room being used.

---

### Post by chrisdeckard on 2008-01-24
gparted is showing you the size of the _partition_, not the _filesystem_.  Big difference.  When you create the filesystem (generally ext3), mkfs reserves 5% (default) of the size for root only.  This makes it so your root partition will show up as 100% full, even though root can still write to the filesystem.  If you didn't do this, bad things could happen such as not being able to boot.  The bigger your partition, the bigger your filesystem, and the bigger that 5% is going to be.

-Chris

---

### Post by Oen386 on 2008-01-24
Interesting, thanks for explaining.

---

### Post by Oen386 on 2008-01-24
Would it be better to use another kind of partition? Other than Ext3, since i am not using it as a boot drive, just external?

---

### Post by chrisdeckard on 2008-01-24
It depends what your needs are.  If you plan to interface with Windoze computers, you may want to configure it with the FAT 32 (LBA) partition type.  When you create the filesystem, make sure you are using a 32-bit FAT or you won't be able to have files larger than 2GB.

$ sudo mkfs.vfat -F 32 /dev/sdb1 (change b to whatever your device is, and 1 to whatever partition you are using)

I don't know the options in gparted, but I'm sure you can do something similar.

If you're only going to use the external drive with your Linux boxen, ext3 is just perfect.  You can pick any filesystem you want, reiserfs, jfs, xfs, or whatever.  FAT is more portable (like what's on a thumb drive).  ext3 is more Linux centric.

-Chris

---

