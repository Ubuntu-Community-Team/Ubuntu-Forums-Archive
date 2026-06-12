---
title: "[SOLVED] tune2fs, fsck, scheduling disk maintenance"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by eks on 2007-09-12
I was trying to use tune2fs to schedule fsck for the next boot, but it did nothing. What I might be doing wrong?

I used:
```

sudo tune2fs -c 30
sudo tune2fs -C 40

```

According to the man page of tune2fs:
```

OPTIONS
       -c max-mount-counts
              Adjust the number of mounts after which the filesystem  will  be
              checked  by e2fsck(8). 

       -C mount-count
              Set the number of times the filesystem has been mounted.  If set
              to a greater value than the max-mount-counts  parameter  set  by
              the  -c  option, e2fsck(8) will check the filesystem at the next
              reboot.

```

Shouldn't it be scheduled for the next boot?

Maybe I'm missing something somewhere else? Because my system doesn't seem to be doing *any* check at all... :-s

And lastly... there really isn't a more "graphical and user-friendly" way to deal with file system checks?


eks

---

### Post by Jose Catre-Vandis on 2007-09-12
Use this to get tune2fs to check a drive on every boot
```
sudo tune2fs -c 1 /dev/hdx
```

where /dev/hdx is the drive/partition you want to check
have a look in your /etc/fstab, or do an "sudo fdisk -l" to see which one you need to check.

The command:
```
sudo tune2fs -c 0 /dev/hdx
```
would mean the drive/partition is never checked (not a good thing!)

[EDIT] for your example, where you are using max count and mount count you need to tell tune2fs which drive/partition as above :)

---

### Post by eks on 2007-09-13
AHA!!!

Thanks a lot!!

Sometimes you just cannot see the obvius (or the obvius is not stated on the man page ;) ).

Just one other quick question, is it possible to use fsck to check a FAT32 partition? Or "not advisable"?


eks

---

### Post by go_beep_yourself on 2007-12-26
Shouldn't these commands only be done to unmounted partitions? That means that you may have to boot your system from a live cd in order to do it, or am I wrong?

---

