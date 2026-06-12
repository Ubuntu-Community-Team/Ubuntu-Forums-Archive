---
title: "Change the home dir"
date: 2008-10-21
forum: General Help
---

### Post by Monotoko on 2008-10-21
Okay, what i want to do, i would think, is fairly simple, but i have no idea how to do it, il also ask a few other questions and explain exactly what im trying to do and why im trying to do it. (I need to get a duel-boot working for my computing course, but i thought id go the extra step and do a little partitioning and explain why iv done it)

Below is my current partition table

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2685    21567231   83  Linux
/dev/sda2   *        2686        3843     9301635    7  HPFS/NTFS
/dev/sda3            3844       29648   207278662+   7  HPFS/NTFS
/dev/sda4           29649       30401     6048472+   5  Extended
/dev/sda5           29649       30401     6048441   82  Linux swap / Solaris
```

As you are probably aware from my partition table, i have 3 usable partition, one linux, and two NTFS

As you can also probably see, two of the spaces are rather small (10GB, and 20GB roughly) These hold Windows XP and Linux, which are currently duel-booting, but i only want these to hold the system files and nothing more.

its /dev/sda3 that i want to hold my other files, its 200GB, and it doesnt have a bootable operating system on it, but can be accessed by both Ubuntu and Windows, which is why i reckon im safe, because if an OS nackers up, i can just format and reinstall without affecting my files or the other OS, right?

In Windows, the large partition is S:\ and i have retargetted the "My Documents" folder to S:\Windows_Resources\MyDocs so now all my documents are held in the shared partition, i also place my program files in there, rather than in the folder Windows gives me on its native C:\ leaqving C:\ for drivers and the OS itself.

How do i do a similar thing in ubuntu? I want /home/monotoko to not be on the main ubuntu OS partition, but instead to be on /dev/sda3 (prefrably in a folder somewhere)

---

### Post by Monotoko on 2008-10-21
bump, anyone? I know its something to do with the fstab file, but i darnt try anything in case i mess it up

---

### Post by tCarls on 2008-10-21
To use another partition you would need to add something like the following line to /etc/fstab:

```
/dev/sda3 /home ntfs defaults 0 0
```

But I'd really recommend not using ntfs as /home under linux. I've never had any problems with it myself but I've heard enough about ntfs write support being buggy that I wouldn't trust it. It also doesn't seem like a good idea to share /home with Windows (although it might not be so bad to mount it at /home/username/Documents instead.)

What I normally do is create a small / partition, a large /home partition, put everything in Windows on one large ntfs partition, and create a small fat32 partition to share between them, resulting in an fstab something like this:

```

/dev/sda1 / ext3 defaults 0 1
/dev/sda2 /home ext3 defaults 0 1
/dev/sda3 /windows ntfs ro,auto,user 0 0
/dev/sda4 /share vfat defaults 0 0

```

Just to reiterate and emphasize, using ntfs for /home and sharing /home with windows sounds like a bad idea and you're likely bound for trouble if you try it. But you're free to try it if you really want to.

---

### Post by sea_monkey987 on 2008-10-21
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ilrudie on 2008-10-22
[COLOR=Red]DO NOT DO THIS[/COLOR].  You shouldn't put important filesystems on NTFS.  It does not support Linux permissions and you will get all sorts of errors if you put your home on it.  The best alternative is to mount the NTFS partition to a non-crucial mount point and sym link whatever folders you want to share into your home directory.

Yes having a seperate /home is a good idea but it should be a Linux native filesystem.

---

