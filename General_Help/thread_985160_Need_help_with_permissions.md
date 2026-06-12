---
title: "Need help with permissions"
date: 2008-11-17
forum: General Help
---

### Post by sumpm1 on 2008-11-17
8.10... storage partition (vfat) is set to mount with all permissions. I followed  this guide: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) . So I have a dev/storage folder that is my extra space on the hard drive. Well, I mounted this space, and installed virtualbox running 2 XP virtual machines, I ran them and everything in one session, no log out. But after a restart, I cannot modify the files in that  /storage folder, I get error: Permission Denied. But that folder IS mounted under root, but neither sudo Nautilus nor sudo chown user works. Can anyone help

---

### Post by geirha on 2008-11-17
That guide you've linked to is for ext3, not vfat. vfat is different because it does not support permissions; and that means chmod and chown won't work. Instead you must set the same permissions and ownership for all files and folders on that filesystem during mount. You do that by setting the option field in fstab to something like this (gives *yourusername* full access, everyone else only read access):

```
defaults,uid=*yourusername*,fmask=133,dmask=002
```

Post your /etc/fstab if you're uncertain.

---

### Post by sumpm1 on 2008-11-17
That seems to have done the trick. Thanks geirha

---

### Post by sumpm1 on 2009-01-09
Alright, I have reinstalled 8.04 i386 today and need to mount my storage partition again and am having problems. I followed everything as done previously. But now I am getting 

```
mount: unknown filesystem type 'dmask=002'
```

when entering the command 

```
sudo mount -a
```

Here is what is in my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e4bdc6fc-8679-437d-a042-7565cdb71dbc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=47186543-e0f9-4208-af1f-2bf540ec322c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda4       /storage defaults,uid=dave,fmask=133,dmask=002
```

---

### Post by logos34 on 2009-01-09
try one of the fstab entries listed [here,]("http://ubuntuforums.org/showthread.php?t=1033286") post #2

---

### Post by sumpm1 on 2009-01-09
Thanks for the reply logos. I found that I was missing the "vfat" line in my fstab, my fault.

---

### Post by logos34 on 2009-01-09
yeah you're right

/dev/sda4       /storage defaults,uid=dave,fmask=133,dmask=002

how did I miss that

---

### Post by sumpm1 on 2009-01-10
Off topic: @logos: Hey, that kitty in your avatar looks just like mine. Is it a bombay cat?

---

### Post by logos34 on 2009-01-10
> **sumpm1 said:**
> Off topic: @logos: Hey, that kitty in your avatar looks just like mine. Is it a bombay cat?

don't know for sure--got him as a stray kitten (along with his brothers).  Although if I had to guess I'd swear he had Russian Black blood--his profile matches almost perfectly.

---

