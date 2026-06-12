---
title: "grub error 17"
date: 2008-10-25
forum: General Help
---

### Post by stldirty on 2008-10-25
ok so I'm triple booting vista and a 32 bit and 64 bit hardy heron. I've been using windows since I got my iPhone though. Today I came home to my laptop being froze while vista was running. I restarted it and decided to boot into Linux. The disk checker came up and gave some error. I don't remember what because I figures a restart would fix it.  That didn't turn out to be the case at all. I rebooted and all i'm getting is grub error 12. Could this be a failed hard drive?  Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-10-25
Sounds like your Ubuntu partition is corrupted, because that would explain your Grub error. If you can boot your Live CD, open a terminal (applications > accessories > terminal), do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then try to do an fsck on it again:
```
sudo fsck -y /dev/sdXY
```
Please post the results of that too.

---

### Post by stldirty on 2008-10-26
> **caljohnsmith said:**
> Sounds like your Ubuntu partition is corrupted, because that would explain your Grub error. If you can boot your Live CD, open a terminal (applications > accessories > terminal), do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then try to do an fsck on it again:
```
sudo fsck -y /dev/sdXY
```
Please post the results of that too.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    94375179    47187558+   7  HPFS/NTFS
/dev/sda2        94381875   113900849     9759487+  83  Linux
/dev/sda3       113900850   135813509    10956330    5  Extended
/dev/sda4       135813510   156296384    10241437+  83  Linux
/dev/sda5       113900913   134801414    10450251   83  Linux
/dev/sda6       134801478   135813509      506016   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

sda5 is the corrupted one i believe

```
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: Attempt to read block from filesystem resulted in short read while reading block 1158

/dev/sda5: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda5

```

---

### Post by caljohnsmith on 2008-10-26
> **stldirty said:**
> 
```
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: Attempt to read block from filesystem resulted in short read while reading block 1158

/dev/sda5: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda5

```
Well, doesn't look good; if fsck can't fix your Ubuntu partition, I think you may have to go for a reinstall. One last thing that you can try would be:
[http://ubuntuforums.org/showpost.php?p=5806996](http://ubuntuforums.org/showpost.php?p=5806996)

But since your fsck didn't complain directly about just a bad superblock, I'm not sure the above thread will do any good, although it won't hurt to try. If you have some files on sda5 that you want to recover, you could use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")". You can download and run it with:
```
sudo apt-get install testdisk
sudo photorec
```
Let me know how it goes.

---

