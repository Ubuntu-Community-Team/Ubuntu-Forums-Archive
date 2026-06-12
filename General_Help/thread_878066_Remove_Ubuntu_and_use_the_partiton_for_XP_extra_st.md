---
title: "Remove Ubuntu and use the partiton for XP extra storage"
date: 2008-08-02
forum: General Help
---

### Post by franzrebs on 2008-08-02
Hi, I'm currently using dual boot (Ubuntu and Windows XP) but I want to uninstall Ubuntu and use that partition for extra storage in XP. Can I do this without having to reformat my XP partition? How do I do this?

---

### Post by Clappy on 2008-08-02
Partition Magic is what I always use when I want to resize partitions. It's awesome and will definitely do what you want it to do. You'll have to perform the action in Windows, then reboot and it will work its magic.

---

### Post by K2712 on 2008-08-02
You will have to reinstall the Windows boot manager using an XP(or Vista) disk via the recovery manager.

From the Windows installation disk, go to the recovery console, and type:

```
fixboot
```

then

```
fixmbr
```

Once that's done, you can use the Windows Disk Management tool to format the partition that Ubuntu is on to an NTFS partition, then it will just show up as another hard drive in My Computer.

---

### Post by jerome1232 on 2008-08-02
> **franzrebs said:**
> Hi, I'm currently using dual boot (Ubuntu and Windows XP) but I want to uninstall Ubuntu and use that partition for extra storage in XP. Can I do this without having to reformat my XP partition? How do I do this?

Well **if** let me emphasize this **if** you have a Windows xp disc you can safely delete the ubuntu partion from windows.

But first I would boot up off the cd when it's done loading things hit 'r' follow the prompts, when you are at the recovery console type 'fixmbr' that command will give windows control of the master boot record again (otherwise deleting ubuntu will make both OS's unbootable)

If you don't have the windows xp cd I'm not sure, I think you can create a boot floopy that can get you into a recovery console but I'd have to boot into windows to find out how.

---

### Post by Clappy on 2008-08-02
Oops, sorry I shouldn't have suggested you use partition magic before fixing your windows boot records. Do that first, and you'll need an XP CD to do it.

---

### Post by astroboy78 on 2008-08-02
Another way:

If you do not have the XP CD and you have a floppy disk drive, get a DOS / Windows 9x-ME bootdisk that has fdisk on it.

Boot with that disk and enter the following command at the a:> prompt

```
fdisk /mbr
```

This command will restore the MS Bootsector and you will be able to boot to Windows. Then use the Disk Management to create a second NTFS partition.

---

