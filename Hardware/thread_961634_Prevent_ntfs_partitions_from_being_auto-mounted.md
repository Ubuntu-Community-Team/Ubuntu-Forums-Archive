---
title: "Prevent ntfs partitions from being auto-mounted"
date: 2008-10-28
forum: Hardware
---

### Post by michluxa on 2008-10-28
Hi,

I have set-up my IBM X31 laptop as a dual boot system (Ubuntu 8.04 and XP Pro). Everything works well using a 250GB WD drive. I created two ntfs partitions (main XP and data) plus the ubuntu swap and ext3 /root and /home.

When I boot into Ubuntu, the two ntfs partitions appear under the top menu item 'Places'. They are mounted under /media/xxx
When I access these, a shortcut is generated onto the desktop.

My question: How can I stop these two partitions to be put automatically under 'Places'. I would prefer a little script to mount/unmount them, as my kids will also use ubuntu and I don't want them to accidentally mess with my Win XP system...

Any ideas, folks?

Thanks,

Micha

---

### Post by jerome1232 on 2008-10-28
I take it these are internal drives? Do your kids have seperate non-admin accounts?

If so then the first thing that comes to my mind is to create an fstab entry that doesn't auto mount the drives and requires root privilegs to mount them.

OR

You can make an fstab entry that makes the drives only readable/writeable by your user.

or you can do both

To edit your fstab type 'gksu gedit /etc/fstab'
```
#an example, noauto makes the drive not mount at boot time 
# nouser only allow root to mount the device, umask=077 only allows the owner of the drive to read/write to it
# uid=1000 set the owner of the drive to the first user of the system
# which I'm guessing is you.
/dev/sdxx /mnt/windowsdrive ntfs-3g nouser,noauto,umask=077,uid=1000 0 0
```

You can read up on options avaible to you for fstab entries [here]("https://help.ubuntu.com/community/Fstab")

---

### Post by michluxa on 2008-10-28
Thanks for your quick reply, my fstab looks like this:

==============================================================

  GNU nano 2.0.7                             File: /etc/fstab                                                                

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1c0fabc2-d98c-45e3-bf3f-dc54580b1347 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4c4c872d-fd73-41a1-8444-fca3a81bff6b /home           ext3    relatime        0       2
# /dev/sda3
UUID=1eec33ff-21b4-49de-9e7e-67b0ad8ad728 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


==============================================================

Unfortunately the two ntfs partitions do not appear here :-(

Any idea what I can do?

---

### Post by michluxa on 2008-10-28
Forgot to mention, yes, my kids will have separate user accounts...

---

### Post by jerome1232 on 2008-10-28
Yeah you'll have to actually add fstab lines for them :) I would suggest finding out what the options actually do rather than blindly copying. Some of the options I think you want would be like this.

nouser,noauto,umask=007,uid=1000,gid=1000

That assumes you are the first user created on the system. If not uid and gid will have to be adjusted.
Feel free to ask questions about the options and such, if you look over that fstab link I gave you, you should be able to piece together what they do.

edit:

So I would add a line like this (adjust to mount where you want it to and adjust the /dev/sdxx to what your's actually is, ask if your unsure
```
/dev/sdxx /mnt/windows ntfs-3g nouser,noauto,umask=007,uid=1000,gid=1000 0 0
```

---

