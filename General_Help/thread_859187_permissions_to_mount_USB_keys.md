---
title: "permissions to mount USB keys"
date: 2008-07-14
forum: General Help
---

### Post by francesco44 on 2008-07-14
Hello Folks,

Hardy seems to work perfectly fine.....EXCEPT....for the mount of external USB keys or HD. More precisely if i use the "double partition" key om which the live ubuntu system is installed the two partitions are detected by the system and appear in the top command board (I installed the mount utility) nexte to the CD-ROM icon.....BUT only the "live" partition Casper-RW is mounted and appear on the desktop. For the other the message is "impossible to mount the volume...bad option...

Obviiously I must give some permission for NTFS or FAT 32 partitions I suppose...but WHERE?

THANKS TO ALL

---

### Post by pytheas22 on 2008-07-14
You shouldn't need to do anything special to mount USB keys.  Just plug them in and you should see an icon for them appear on your desktop.  NTFS partitions of the hard drive can be mounted by selecting them from the Places menu.  You don't need to do anything else if you're using Hardy.

Did you install Ubuntu to disk yet?  If you're still on the live CD, install Ubuntu, and then plug a USB stick into your computer.  Immediately after, please open a terminal (under Applications>Accessories) and type:
```

dmesg
cat /etc/fstab
```

and post the output of those commands here (the first will be long but just post as much of it as you can).  If there's a bug that's preventing disks from being mounted like they should, this will help get to the bottom of it.

---

### Post by francesco44 on 2008-07-15
Thanks Pytheas,

I will do it tomorow...but anyway I noticed that under "system" menu there is an authorisation item (or may be permissions I work on a french version of 8.04)  with a long list of possibilities....I suppose this might be ill configured because my live system is on a USB Key ....from Dragon tech....

---

### Post by pytheas22 on 2008-07-16
What is the item called in French?  In the English menu there is a "users and groups" option where you can set permissions for all of the users.  But by default all users should be able to mount the USB keys that they insert.

Maybe there's some problem with the way you installed Ubuntu, though.  To confirm: you didn't install it to hard disk; it's all running from a USB stick?

---

