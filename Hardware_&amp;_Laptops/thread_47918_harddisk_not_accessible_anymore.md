---
title: "harddisk not accessible anymore"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by mephisto56 on 2005-07-10
Today, after rearranging some free partitions with acronis partition manager, I rebooted and my harddish wasn't accessible anymore. It's still recognized (eg knoppix, which I'm using now to get online, recognizes a hd) but no program can access it anymore. My bios mentions the harddisk.
Something must have gone wrong and I hope to be able to get it working again but have no clue as to what I might try.

suggestions really really appreciated.

---

### Post by Dogmeat on 2005-07-10
To be able to help you we must know a couple things first:

What do you mean by not accessible, you can't boot it or you can't mount it from knoppix?
What filesystem was it using (ext3, reiserfs, NTFS)?

---

### Post by mephisto56 on 2005-07-10
[QUOTE=Dogmeat]To be able to help you we must know a  couple things first:

What do you mean by not accessible, you can't boot it or you can't mount it from knoppix?
What filesystem was it using (ext3, reiserfs, NTFS)?[/QUOTE]

Hi Dogmeat and thanks for taking your time for helping me.
To answer your questions:

Not accessible : can't boot nor mount (or I must be mounting it the wrong way if it differs from ubuntu, anyway knoppix can't get into hda)

Filesystem : reiserfs, ntfs and fat32 depending on the partitions (had windows xp and ubuntu)

edit: I can't see any files (nor partitions) from knoppix, windows nor ubuntu start since the boot process hangs with a disk failure

---

### Post by Dogmeat on 2005-07-10
[This person](http://www.softwaretipsandtricks.com/forum/showthread.php?t=21758) had the same problem as you, try following their tips!

---

### Post by mephisto56 on 2005-07-10
Again thanks for the reply. My situation is a bit more different (and hopeless I'm afraid) from that person, since I can't access anything anymore. No partitions are recognized, nothing can be booted, read etc. The only thing that gives me hope is that my bios still reports my maxtor, knoppix finds a hda0 and windows install knows how many gb it is. Though none of those can access it. I'm afraid I'll have to buy a new one and try my current as slave to restore some files.

---

### Post by Dogmeat on 2005-07-10
Are you sure it's physically damaged? Didn't that happen when you tried installing ubuntu? I saw some people around saying grub screwed up their windows boot! 

Anyway.. if you just want to recover some files, your best bet is trying to mount it with knoppix (I never used it, but the mount command is probably the same: mount -t ntfs /mnt/windows /dev/hdxy (where x is your hard drive letter and y your windows partition, i.e.: /dev/hdc0)

You can find out which one it is by typing sudo fdisk -l.

You said you tried mounting it already, what error did you get? If you can paste the fdisk and mount outputs here it would help!

---

### Post by mephisto56 on 2005-07-10
I'm not yet sure it's physically damaged. Mounting doesn't work either, fdisk -l outputs nothing. I still hope acronis partition manager f*cked up and the result is recoverable. So far no luck.

---

### Post by Dogmeat on 2005-07-10
Did you try fdisk as superuser?? if you do fdisk -l as a regular user it will output nothing! If as root it still doesn't show anything.. getting your data back will be rather hard unless you use some hd forensic tools. If you just want your hard drive back, i'd try zerofilling it with a vendor specific program

---

### Post by mephisto56 on 2005-07-11
Some of the sectors seem to be damaged. Also sector 0. I'll buy another disk and try to recover some files with my current drive as slave.

---

