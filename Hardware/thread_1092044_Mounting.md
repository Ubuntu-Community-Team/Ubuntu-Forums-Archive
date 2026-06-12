---
title: "Mounting"
date: 2009-03-10
forum: Hardware
---

### Post by MissKitty on 2009-03-10
I'm new to Ubuntu, in fact I'm new to Linux all together! I'm no dummy when it comes to computers though, as in windows.
I don't know how to get Ubuntu to mount my usb flash drive. It wont mount by its self and when I click on the drive for it to mount, it tells me I can't mount it.
How do I get it to mount (and unmount) my flash drive?
Also how do I get it so not just the root user can mount and unmount?
:?

---

### Post by _BigWings_ on 2009-03-10
i have the same problem, only the root user can mount and unmount and also it seems like only the root user can write to a mounted drive.

I'm also new to ubuntu and haven't gotten the hang yet of all this root user/permission stuff that seems to be popping up every 3 seconds :(

---

### Post by MissKitty on 2009-03-10
> **_BigWings_ said:**
> i have the same problem, only the root user can mount and unmount and also it seems like only the root user can write to a mounted drive.

I'm also new to ubuntu and haven't gotten the hang yet of all this root user/permission stuff that seems to be popping up every 3 seconds :(


Yay! I'm not the only one in this club!
A friend of mine is going to school for all this fun stuff and is trying Ubuntu out on the side. Since I'm a computer geek myself (more on the programming side of it all) he thought he'd give it to me to try out too. So together we are trying to master Linux. I'm stuck and have no idea what I'm doing and my friend is in bed already. I'm SOL right now lol! If I only knew the commands for the command line I'd be fine. Linux is nothing like windows when it comes to this stuff.

---

### Post by Kang on 2009-03-10
First, create a directory where the USB drive will be mounted, e.g.:

```
$ sudo mkdir /media/USB
```

Then mount the drive:

```
$ sudo mount -t vfat /dev/sdx/ /media/USB
```

where /dev/sdx is your USB drive. You can usually figure this out with:

```
$sudo fdisk -l
```

Alternatively, you can enable specific users to mount external drives without root privileges: System->Administration->Users and Groups. Click unlock, enter password. Then select a user click properties and go to User Privileges tab. Check the box next to "Access external storage devices automatically".

Let me know if it helped!

---

### Post by MissKitty on 2009-03-10
Ok well it's not going that well. I told it to mount using the code you gave me and it told me that mount: special device /dev/sdx/ does not exist. So I looked at last code you gave and I thought ok maybe it's the type of drive I'm telling it to mount. I used the last code and got this:

```

root@Linux:/# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd66dd66d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  27  Unknown
/dev/sda2   *        1021       14232   106119953    7  HPFS/NTFS
/dev/sda3           14233       19457    41969812+   5  Extended
/dev/sda5           14233       19237    40202631   83  Linux
/dev/sda6           19238       19457     1767118+  82  Linux swap / Solaris

Disk /dev/sdb: 2079 MB, 2079850496 bytes
255 heads, 32 sectors/track, 497 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         498     2031088    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 254, 32) logical=(497, 208, 32)
```

So my next step was this:

```

root@Linux:/# sudo mount -t vfat /dev/sdb/ /media/USB
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Am I on the track with the change that I made?

I'm kinda lost. Not sure what some of this means. Oh and can I leave out "sudo" since I'm in root user? Sudo is only used when I'm under a normal user and trying to do a root command, right?

I'm going to keep playing with this till I get a word back.

---

### Post by taurus on 2009-03-10
Try adding a 1 in there and see what happens.

```
sudo mount -t vfat /dev/sdb**[COLOR="Blue"]1[/COLOR]** /media/USB
```

p.s.  You shouldn't be logged in as root!  It's dangerous if you don't know what you are doing.

---

### Post by MissKitty on 2009-03-10
OMG! I did it! I mounted it! I think I got it!

I changed my code to:

```
sudo mount -t vfat /dev/sdb1/ /media/USB
```

Yay!

I'm slowly starting to get this. Thank you soooo very much!

But I still have that last question about when to use sudo. Also I just want to make sure I understand what I did there...

sudo       = root user
mount      = Telling that I want to mount.
-t         = I have no idea what this means.
vfat       = The system type that I'm trying to mount. This will either be vfat or ntfs.
/dev/sdb1/ = Where the drive is that I wish to mount.
/media/USB = Where I want it to mount to/open in.

Now I'm going back to see if I can mount this puppy in my normal user.

---

### Post by taurus on 2009-03-10
```

       -t vfstype
              The  argument following the -t is used to indicate the file sys-
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs,  ext,  ext2,  ext3,  hfs,  hfsplus,  hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, smbfs, sysv, tmpfs,  udf,  ufs,  umsdos,
              usbfs,  vfat,  xenix,  xfs, xiafs.  Note that coherent, sysv and
              xenix are equivalent and that xenix and coherent will be removed
              at  some  point  in  the future &#8212; use sysv instead. Since kernel
              version 2.1.21 the types ext and xiafs  do  not  exist  anymore.
              Earlier,  usbfs  was  known as usbdevfs.  Note, the real list of
              all supported filesystems depends on your kernel.

```

---

### Post by Kang on 2009-03-10
> **taurus said:**
> Try adding a 1 in there and see what happens.

```
sudo mount -t vfat /dev/sdb**[COLOR="Blue"]1[/COLOR]** /media/USB
```

Yes, that should probably do it, my mistake :oops:

> p.s.  You shouldn't be logged in as root!  It's dangerous if you don't know what you are doing.


Agreed. 

Did you check out the other option, it certainly is a faster way to do it each time!

---

### Post by Kang on 2009-03-10
> OMG! I did it! I mounted it! I think I got it!

Congrats, you're on the right track!

---

### Post by MissKitty on 2009-03-10
Thanks Kang and taurus! You have both been a big help.

---

