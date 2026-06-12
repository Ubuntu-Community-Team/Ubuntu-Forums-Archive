---
title: "mount drive in read-only mode"
date: 2008-05-28
forum: Hardware
---

### Post by Wej on 2008-05-28
How can I mount my 8.04 server disk as read only? Once I get it completely configured, I do not want to write to the CF card anymore. Here is my entire /etc/fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3cc4dc7e-7f09-49fd-b6de-06efe16a865d /               ext2    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Should I just replace the "errors=remount-ro" with "ro" to make it always read-only?

---

### Post by didac on 2008-05-29
Not that I'm an expert, but a read-only hard disk will not be writable by anybody, not even the operating system, so it won't work. Maybe you want to protect some folders so that are not writable?

errors=remount-ro means that when it's booting, if the the hard disk check finds errors it will remount the filesystem as read-only and you take it from there.

'Methinks' you should leave it as it is and explain why you want a read-only filesystem.

---

### Post by Wej on 2008-05-29
It is going to be an embedded device. It will not require any changes to it. I want it to be read only so that if something does happen to try and write to the disk, it will fail. The OS shouldn't need to write to the disk, only read from it. My plan was to mount the /var directory on a ramdisk so that it could have write access but will not save that data after a reboot. Having a read only system disk will accomplish a few things:
[list]
[*]Be able to switch device on and off without worrying about hurting the file system by turning it off in the middle of a write. No fsck needed since the FS can't become corrupt.
[*]If system is compromised by something like a trojan or virus somehow, restarting the system will clear the ram of its contents and it will be a fresh load.
[*]It will stop the casual IT worker/hacker that has access to the system from logging in and making unwarranted changes. I know it won't stop someone who knows how to re-mount the system disk with read-write permissions.
[*]Increases the lifetime of the compact flash device that the OS is installed on. It should last plenty long enough running ext2 in regular mode, but I rather know that the flash is going to last 100 times longer than the board ever will.
[/list]
We currently do this now with our embedded Windows devices, using the EWF extension of XPe. This device I am building and configuring needs to do some complicated routing over multiple interfaces that is quite difficult to achieve in Windows where as OLSR + Linux makes it a breeze.

---

### Post by didac on 2008-05-30
Crystal clear explanation. 

Then modify your /etc/fstab to read:

```
UUID=3cc4dc7e-7f09-49fd-b6de-06efe16a865d /  ext2 relatime,errors=remount-ro,ro 0 1
```

It should be enough

---

### Post by Wej on 2008-05-30
Thanks, I'll try that out on my test system.

---

