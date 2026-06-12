---
title: "Hard drive died, and I'm a backupless idiot, but is there hope?"
date: 2012-01-20
forum: Hardware
---

### Post by Asday on 2012-01-20
My PSU blew not too long ago, and a replacement PSU seemed to fix everything, but today, the PC died a stuttery death, and then failed to boot, as the HDD the OS resides on was unrecognised.  Post cable-jiggling, the BIOS can see it, and read it's model number, and I get this screen in "Disk Utility":

[img]http://i.imgur.com/tvO2W.png[/img]

The fact it can see how big the partitions were makes me have some hope.  That 483GiB is exceedingly important to me, (though obviously not important enough for me to realise I should *back it up*).

What's wrong with it, and is there any way to get it back?

EDIT:  Talking with a friend yielded this:

```
ubuntu@ubuntu:~$ sudo mkdir hope
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /hope
Error reading bootsector: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ubuntu@ubuntu:~$ sudo fsck.ntfs /dev/sda2
sudo: fsck.ntfs: command not found
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 

```

---

### Post by wyliecoyoteuk on 2012-01-20
Testdisk might help:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Asday on 2012-01-20
> **wyliecoyoteuk said:**
> Testdisk might help:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Apparently that's in the repos, and you made me try to compile it, you cruel and unusual man.

But back in serious land, it whizzed through the cylinders, and came out with read errors everywhere.  Does that mean anything?

EDIT:  I dunno what I did, but it's fixed.  I immediately started backing up my important stuff, and sometimes it crashed out, saying something about insufficient resources, but I have backup now, so it's coo'.

---

### Post by Hedgehog1 on 2012-01-20
**Glad you were able to save the data!**

I just copied a work-mates data off a badly damaged laptop.  I got the drive to "It's alive" state just long enough to pull the 98% of the data that could still be read around the 1201 damaged sectors when the laptop impacted.

The drive promptly died for good about 30 minutes later.

***The Hedge***

:KS

---

### Post by Asday on 2012-01-20
I like your text decoration.

Mine hasn't died yet; infact I'm running my OS off it, so I dunno what was wrong with it, or what fixed it, but YAY.

---

