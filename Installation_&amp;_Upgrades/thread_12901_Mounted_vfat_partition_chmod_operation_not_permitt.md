---
title: "Mounted vfat partition: chmod operation not permitted"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by Shambler on 2005-01-27
I have a special hard drive for storing my data and mounted it with the following /etc/fstab settings:
```

/dev/sda1     /mnt/data1     vfat     users,umask=0,auto     0     0

```

But when I want to copy files with Midnight Commander to /mnt/data1, mc tells me the following:

```

cannot use chmod. operation not permitted!

```
Well, something like that, since I have german locales installed, but I think you can guess what it is...

Any suggestions?

---

### Post by rudi on 2005-01-27
Change your fstab entry to:
   ```

    /dev/sda1     /mnt/data1     vfat umask=000      0      0
    
```

---

### Post by Shambler on 2005-01-30
I still got the same problem...

---

### Post by Sirenian on 2005-01-31
I did this yesterday!

Here's what I did:

sudo gedit /etc/fstab
change fstab line as post above (I had gid 100, uid 1000 (me), not sure if uid important but I was desperate)
add myself to "users" group (that's the 'gid 100')
log out, log in again

Now you should be able to access the partition. More information on mounting windows partitions can be found at:
[http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions/view?searchterm=mount%20windows%20fat32](http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions/view?searchterm=mount%20windows%20fat32)


You may also have some luck doing "sudo chmod" before these changes, but I wouldn't bet on it.

---

### Post by Shambler on 2005-01-31
Which post above do you mean?

---

### Post by kultex on 2005-01-31
try to change your fstab to

 /dev/sda1     /mnt/data1   vfat  auto,uid="username",umask=0002   0    0 

username can be your username or your number, which is default 1000, when its only you

start the computer new and it should work


if this does not work - go to your directory click right  -  go to the last entry - properties (in english?) - and look under - i hope it is rights ? what you are allowed - read - write - execute?

If you as a user can do now everything - then we should report a bug - because I in my case have all rights and I can not do a linkage to a  file - in german I get - not allowed to do this (direct translation)

---

### Post by Shambler on 2005-01-31
Ok, this worked for me:
```

/dev/sda1	/mnt/data1	vfat	defaults,auto,uid=1000,gid=1000		0	0

```

---

