---
title: "Formatted Iomega external hd to ext3 but can't put files on it"
date: 2013-02-09
forum: Hardware
---

### Post by rapattack1 on 2013-02-09
Hi i was given this secondhand 500gb Iomega hard drive and i formatted it to ext3 but i can't paste any files on it. Did i miss something? I used gparted

---

### Post by tgalati4 on 2013-02-09
Creating partitions is a two step process:

1. Mark the partition with a label and type.
2. Put a file system on it that matches the type.  This is known as "formatting" or "making the file system."

mkfs is the tool to do that.  You can mark "format" in some partitioners, or you can do it manually:

Open a terminal: (This is a destructive command, make sure that you have the correct partition and you have backups of any data on the this drive.)

```
sudo mkfs /dev/sdg1
```

You may have to unplug the drive and plug it back it for the operating system to recognize it.

---

### Post by dabl on 2013-02-09
> **rapattack1 said:**
>  Did i miss something? I used gparted

You didn't miss anything -- you just didn't finish the job.

Storage devices and their filesystems are, by default, owned by root.

Open your file manager (nautilus?) with "gksudo" privileges, browse to your plugged-in and running external drive, and make a new folder on it -- pick a name that means something, like "VIDEOS".

Now use your file manager (still running under "gksudo") and change the owner and permissions to yourself (or "users") on the new folder.

Afterward, you (the user) should be able to browse to the mounted drive and access the folder.

---

### Post by rapattack1 on 2013-02-10
Thanks for the replies. Sorry can you go step by step for me. I know the terms but not the meaning and well the rest is just not registering in my brain with either posts. I know what a label is but have never done one. Formatting before an install of an OS yes i know but always found formatting externals a hard task. Always took so long that by the end of the process i have forgotten the lot.
As for permissions i know what that is but used so many linux distros it seems so different in everyone on. I am not fabulous with fine details so i need them please.
Oh i know how to get the file manager but don't know where to type gksudo.
Thanks!

---

### Post by dabl on 2013-02-10
I'm a KDE user, so I'm not certain about Gnome, but I think you'll press Alt-F2 and in the window type "gksudo nautilus" with no quote marks.  If that works, and if the Iomega is mounted (is it?) then you can browse to it, right click and choose "new" and then "folder" and then type the name of your data folder.  Once that is done, you right-click on the new folder, choose "properties", then change the owner from root to your user name, or "users" if other people are to have access to it, and the same for groups.  Permissions should be set to read and write.

By the way, before you unplug or power off the Iomega, every time you need to browse to it and click "safely remove" or you will soon trash that ext3 filesystem.

---

### Post by rapattack1 on 2013-02-11
Wow thanks so much that did the trick. Oh yes i always so a safe removal although i notice this version of ubuntu studio has those eject icons like macs do. I dunno if it is because the system is xfce?

---

