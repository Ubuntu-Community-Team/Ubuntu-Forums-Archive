---
title: "Failing hard drive, won't mount, need files"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by Riceboy004 on 2007-12-22
I was running a dual boot of Gutsy and XP on my Averatec Laptop, it's about 3 years old.  It appears that my hard drive is going bad and will not mount.  I really do not care if I get this hard drive running stable, I just need some way to pull my data off of it!  Here's the story...

1. I came to my room to find that the laptop screen was blank, and it was apparently frozen
2. I did a hard shut off and turned it back on
3. Grub started loading, it gave me Error 18
          (apparently this is an issue of using a newer hard drive with an older bios.  This is obviously not my case, since this system has been working before.)
4. Booted to Ubuntu Live Cd, tried to mount my ubuntu partition, gave me this error
```

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[ 3305.296000] lost page write due to I/O error on sda2
[ 3305.296000] ata1: EH complete
[ 3305.296000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[ 3305.300000] sd 0:0:0:0: [sda] Write Protect is off
[ 3305.300000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3305.308000] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3305.312000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[ 3305.316000] sd 0:0:0:0: [sda] Write Protect is off
[ 3305.316000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3305.320000] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
```

5. I've tried to make a backup using dd and ddrescue with no success
6. I used testdisk to locate backup superblocks.  I attempted to replace the superblock with fsck, but fsck gives me error
6. Simply trying to have fsck fix my drive doesn't either

```
ubuntu@ubuntu:~$ sudo fsck -a -t ext3 /dev/sda2
fsck 1.40.2 (12-Jul-2007)
/dev/sda2: recovering journal
/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 19558

JBD: Failed to read block at offset 17995
fsck.ext3: Input/output error while recovering ext3 journal of /dev/sda2

```

Any ideas?  I don't necessarily need to get this drive up and running stably, I just have some important documents that i need.

Thanks

---

### Post by pyronaut on 2007-12-22
hi try the slueth kit ... and this link might help
[http://linux.sys-con.com/read/117909_2.htm](http://linux.sys-con.com/read/117909_2.htm)
 i was scratching my head for a way to undelete a couple of really important files and this helped

---

### Post by Ocxic on 2007-12-22
this sounds nutz but it works, take your hard drive out of your computer, place in a plastic bag, and place in freezer for a few hours, then quickly place hard drive back into computer and remove the data you need as fast as possible, this may work a few times. looks like your drive is failing, happened to me a while ago.

---

### Post by Sef on 2007-12-22
Download [Knoppix]("http://knoppix.com").  And with a usb drive, you might be able to get the data off your disk.

---

### Post by Riceboy004 on 2008-01-06
sorry about the delay, I've been on vacation...

Here's my update.
I tried the knoppix cd, it boots, starts loading, then hangs after the line:

Scanning for Harddisk partitions and creating /etc/fstab... Done.

Then there is nothing.  My harddrive light is on and i can hear it spinning away.

Any other suggestions?  Before I take apart my laptop and try to put it in the freezer, does anyone know any way I could just mount the hard drive by brute force so I can get my school documents?  Like i mentioned before I dont need stability.

Thanks I appreciate your help.

---

### Post by c0met on 2008-01-07
I don't know if this will help. SuperGRUB might help you boot up so that you can read the drive. It's quite a powerful little program. It's at...

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Riceboy004 on 2008-01-14
> **c0met said:**
> I don't know if this will help. SuperGRUB might help you boot up so that you can read the drive. It's quite a powerful little program. It's at...

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

I've tried supergrub, no success.  Gives me a bunch of input/output errors

I just tried putting the harddrive in the freezer for a few hours.  No luck :( still the same error.
I'm about to give up.  Anyone have any other suggestions?

---

