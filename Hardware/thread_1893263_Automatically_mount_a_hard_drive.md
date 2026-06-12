---
title: "Automatically mount a hard drive"
date: 2011-12-09
forum: Hardware
---

### Post by baldurmen on 2011-12-09
Hi!

I've recently added a slave to my computer, and I can't manage to get an automatic mount working properly...

The disk is all formated and everything (via terminal), I just need to change the values in fstab.

This is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9ddf361a-501f-4a16-ac2b-bfccf86906a4 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=83af586a-3a07-41fc-bd00-90c7be6d6fe6 none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=9715f991-17f0-4c76-8bff-1e51acbc732f /media/sdb1   ext3    defaults     0   $   2

```


The drive I'm trying to get mounted is 9715f991-17f0-4c76-8bff-1e51acbc732f , placed in /media/sdb1 , formated in ext3

Could someone explain to me what's wrong with my code and why it's wrong? I'm not an expert, but I'm slowly starting to play (more seriously) in the terminal.

---

### Post by baldurmen on 2011-12-09
Pff. I got kind of mixed between drives. So here's the drive (real) infos:

/dev/sdb1
/media/Personal
ext3

Truly, I don't know what's its UUID, so if someone could also help me with getting that...

Here's what I coded into fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9ddf361a-501f-4a16-ac2b-bfccf86906a4 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=83af586a-3a07-41fc-bd00-90c7be6d6fe6 none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/Personal   ext3    defaults     0        2

```

Yet, it still doesn't work.

---

### Post by searchfgold6789 on 2011-12-09
Have you tried making sure te mount point /media/Personal was actually there and all the permissions were set correctly? (sudo chown -R {username} /media/Personal)

---

### Post by baldurmen on 2011-12-10
I had already "chown -R username:username"  my disk to be sure I could modify it as I wished.

---

