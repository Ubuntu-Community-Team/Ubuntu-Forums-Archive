---
title: "failure to mount USB drives"
date: 2011-04-06
forum: Hardware
---

### Post by hadjimurad on 2011-04-06
I'm having a moderate annoyance with a USB thumb drive. It fails to mount automatically, so every time I want to use it I have to go through the command line and do that manually. I have another external hard drive which mounts automatically just fine -- it's particular to this thumb drive.

When I try to use the Disk Utility and hit the "Mount" button, I get the following error message:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

```

If it helps, here's my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=36d9165e-2290-4df0-9672-b962682d563c none            swap    sw              0       0

```

The thumb drive is associated with sdb1. My first guess is to delete that line -- maybe fstab is directing it to the wrong mount point. I'm hesitant to monkey around with fstab though, is this what I should be doing?

---

### Post by Finnius on 2011-04-07
Hey,

Try this:

```
cd /media
sudo mkdir Windows (or whatever you want it to be called)
sudo umount /dev/sdb1
sudo mount.ntfs-3g /dev/sdb1 /media/Windows
```

Saw the above fix on another thread:
[HTML]http://ubuntuforums.org/archive/index.php/t-1607680.html[/HTML]

There have been a few people getting your problem sorted out this way...seems its trying to mount over your OS drive /sda1.

Hope it helps

---

