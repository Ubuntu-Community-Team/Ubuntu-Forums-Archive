---
title: "New hard drive permission question"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by ravid on 2009-01-31
Hey everyone, 

I've just installed a new seagate 1tb sata drive.  I have it installed fine, fstab is update and it mounts fine.  However I was curious how to get the hard drive to be writable by me WITHOUT changing the owner/group on the mount point (it obviously writes fine if i change the owner/group to myself).  

I only ask this, because during installation I mount one of my other two harddrives at /srv.  My /srv drive permissions are set to root:root however I'm still able to write to that as my regular user.  I have copied the exact fstab entry from /srv and duplicated it and changed the UUID to the new drive.  Is there something else on the system that controlling my permissions to write there? And how do I get my new HDD to act the same way?

250gb HDD mounted to /srv
1000gb HDD mounted to /srv2

Any help is appreciated.
Cheers, 
Ravid

FSTAB:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=79b8cde0-0c5f-411b-979b-0e653d6b3826 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=0d4c2bf3-7e12-4429-bfae-695a3b850427 /home           ext3    relatime        0       2
# /dev/sda1
UUID=0dc1877a-7017-4280-aab6-edec66e7d8ce /srv            ext3    relatime        0       2
# /dev/sdb2
UUID=6ae36403-ab4d-413d-bce9-2eac15fca9c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=5e42aa77-ae53-476f-a192-3157bfd19c7e /srv2            ext3    relatime        0       2

```

Output of blkid:
```

/dev/sda1: UUID="0dc1877a-7017-4280-aab6-edec66e7d8ce" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="79b8cde0-0c5f-411b-979b-0e653d6b3826" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: UUID="5e42aa77-ae53-476f-a192-3157bfd19c7e" SEC_TYPE="ext2" TYPE="ext3" LABEL="bigboy" 
/dev/sdb2: TYPE="swap" UUID="6ae36403-ab4d-413d-bce9-2eac15fca9c2" 
/dev/sdb3: UUID="0d4c2bf3-7e12-4429-bfae-695a3b850427" SEC_TYPE="ext2" TYPE="ext3" 

```

---

### Post by taurus on 2009-01-31
Maybe you have set permissions of /srv to 777.

```
ls -la /
```

---

### Post by ravid on 2009-01-31
Nope... 

```

drwxr-xr-x   9 root root  4096 2008-10-29 19:50 srv
drwxr-xr-x   4 tim  tim   4096 2009-01-31 22:20 srv2

```

(note I have changed the mount point to my user in the meantime so i can actually start to use the drive)  :)

---

### Post by taurus on 2009-01-31
Are you sure you can write to /srv when you log in with your username--tim?

```
touch /srv/testing
```

---

### Post by ravid on 2009-01-31
okay thanks for the quick response but apparently I'm on crack  :)  I DO have to change the permissions... however the reason I was asking was because it DID allow me to touch a file without sudo'ing...  then it dawned on me that that file already existed and was owned by me  :) 

Anyway thanks again for your help.

---

