---
title: "[SOLVED] Can't write to hard drive after changing from NFTS to ext3."
date: 2008-08-28
forum: Hardware
---

### Post by erudite on 2008-08-28
I used gparted to change my second HDD from NTFS to ext3.  After doing this I couldn't seem to unmount.  So I then rebooted and I could unmount fine however when i tried to write data it doesn't let me.

If I use sudo command and cp it works but this is annoying.  When I try and delete the file I just copied using the sudo command I get the "Permission Denied" error.  Also...when I check disk properties it says "You are not the owner, so you can't change these permissions."  

What do I have to do to be able to have read write privileges again?

---

### Post by hessiess on 2008-08-28
if its an internal drive you need to add 'nosuid' to /etc/fstab.
```

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


#/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
#/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
UUID=04c474f0-5bb7-46af-8696-38af01ba1615 / ext3 noatime,defaults 0 1
UUID=6f9a782a-f050-4912-b7ad-15cc9c07c656 swap swap noatime,defaults 0 0
# data partition
/dev/sda7 /home/a/ALL                                     ext3   noatime,nodev,nosuid     0       2
```

---

### Post by stchman on 2008-08-28
> **erudite said:**
> I used gparted to change my second HDD from NTFS to ext3.  After doing this I couldn't seem to unmount.  So I then rebooted and I could unmount fine however when i tried to write data it doesn't let me.

If I use sudo command and cp it works but this is annoying.  When I try and delete the file I just copied using the sudo command I get the "Permission Denied" error.  Also...when I check disk properties it says "You are not the owner, so you can't change these permissions."  

What do I have to do to be able to have read write privileges again?

You need to give your user ownership of the drive.

Do this:

```

sudo chown -R $USER:$USER <mount point>
chmod -R 755 <mount point>

```

Substitute the <mount point> for where you actually mounted the drive.

Did you make sure and make the proper entries in your fstab?

---

### Post by erudite on 2008-08-28
Ok so I did what you said stchman.

No I haven't edited my fstab since changing from NTFS.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5d4a0c33-f40c-450e-97cb-f50e88afa870 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=30f0e107-a124-49f6-a530-b64361c1e3c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

My mount point is /media/disk.
My device name is /dev/sda1.

What line do I need to add to fstab?

Thanks for you help so far people.

---

### Post by mary900 on 2008-11-02
erudite -- I have your exact same problem with exact same mount point. What line did you add to your fstab??

Thanks for your help>

---

### Post by erudite on 2008-11-02
Hiya Mary,

I added [quote=fstab]/dev/sda1 /media/disk ext3 defaults 0 0[/quote].

Hope this helps.

Thanks,
Josh

---

### Post by timmahhny on 2008-11-03
> **stchman said:**
> You need to give your user ownership of the drive.

Do this:

```

sudo chown -R $USER:$USER <mount point>
chmod -R 755 <mount point>

```

Substitute the <mount point> for where you actually mounted the drive.

Did you make sure and make the proper entries in your fstab?

Thanks this helped me a great deal as well. I need to keep a cheat sheet.

---

