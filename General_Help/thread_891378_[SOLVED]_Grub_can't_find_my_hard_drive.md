---
title: "[SOLVED] Grub can't find my hard drive"
date: 2008-08-16
forum: General Help
---

### Post by dodle on 2008-08-16
When I try to boot up I get thrown into the BusyBox shell.  In grub, I've tried replacing "UUID=d286688a-8587-4977-99b9-1414cf09c374" with "/dev/sda5" and "/dev/hda5" but nothing works.

```
ALERT! /dev/disk/by-uuid/d286688a-8587-4977-99b9-1414cf09c374 does not exist.
Dropping to a shell!
```

---

### Post by iaculallad on 2008-08-16
> **dodle said:**
> When I try to boot up I get thrown into the BusyBox shell.  In grub, I've tried replacing "UUID=d286688a-8587-4977-99b9-1414cf09c374" with "/dev/sda5" and "/dev/hda5" but nothing works.

```
ALERT! /dev/disk/by-uuid/d286688a-8587-4977-99b9-1414cf09c374 does not exist.
Dropping to a shell!
```

Boot using recovery mode and try to find the correct UUID of your partition:

```
sudo blkid
```

And replace your existing configuration on your fstab file.

---

### Post by dodle on 2008-08-16
I don't have an option to boot into recovery mode (don't want to go into why either), can you tell me how to edit the line in grub?

Or, is there a way to find the UUID from the grub shell?```
grub>
```

---

### Post by iaculallad on 2008-08-16
> **dodle said:**
> I don't have an option to boot into recovery mode (don't want to go into why either), can you tell me how to edit the line in grub?

Or, is there a way to find the UUID from the grub shell?```
grub>
```

Try using your LiveCD instead.

---

### Post by dodle on 2008-08-16
I've booted into a live cd but I don't know how to find the uuid of a partition.  Is there a way to find it?

---

### Post by dodle on 2008-08-16
> ```
sudo blkid
```

And replace your existing configuration on your fstab fileSorry, I didn't pay much attention to that command.  Thanks.  I'll try that.

---

### Post by dodle on 2008-08-16
According to blkid the uuid that the system is trying to boot with is the correct one.  So why won't it boot?  Can I get a different Kernel somewhere?  Would that help?

---

### Post by iaculallad on 2008-08-16
> **dodle said:**
> According to blkid the uuid that the system is trying to boot with is the correct one.  So why won't it boot?  Can I get a different Kernel somewhere?  Would that help?

Try posting your:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab

```

---

### Post by dodle on 2008-08-16
fstab> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=d286688a-8587-4977-99b9-1414cf09c374 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=3ed226c7-7a51-49e7-a82a-86a87241794d none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
## Windows
# /dev/hda1 -- converted during upgrade to edgy
UUID=42A8BB1DA8BB0E83 /windows ntfs defaults 0 0
blkid> ubuntu@ubuntu:~$ blkid
/dev/hda5: UUID="d286688a-8587-4977-99b9-1414cf09c374" SEC_TYPE="ext2" TYPE="ext3"
fdisk -l> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7916    63583978    7  HPFS/NTFS
/dev/hda2            9359        9729     2980057+  49  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda3            7917        9358    11582865    5  Extended
/dev/hda5            7917        9231    10562706   83  Linux
/dev/hda6            9232        9358     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by iaculallad on 2008-08-16
```
gksudo gedit /etc/fstab
```

Replace the line of text below on your fstab file:

```
UUID=d286688a-8587-4977-99b9-1414cf09c374 / ext3 defaults,errors=remount-ro 0 1
```

with this one:

```
UUID=d286688a-8587-4977-99b9-1414cf09c374 /               ext3    defaults,errors=remount-ro 0       1
```

Do a copy and paste method. Save and Close the file. Do a reboot to test.

---

### Post by caljohnsmith on 2008-08-16
Iaculallad, that second line you gave dodle to replace in his fstab is exactly like the one he all ready has, except with added spaces. That shouldn't make any difference. Was that a mistake or did I miss something?

Dodle, when you run blkid, you need to make sure you run it as root. Please post:
```
sudo blkid
```
And also please post:
```
cat /boot/grub/menu.lst

```

---

### Post by dodle on 2008-08-16
I decided to do a fresh install of ubuntu.  I was having all kinds of problems, and now I am faced with a new one.  Dapper is the only version that I can get to install correctly on my laptop, but I wanted Hardy.  So, I tried to do an upgrade, but I think I did it wrong.  Now I've got all kinds of broken packages and I cannot start an X session.  Is there anything I can do, or should I give up on my laptop?  I've been spending waaaay too much time trying to get this thing up and going, when I could be studying Python.

---

### Post by caljohnsmith on 2008-08-16
Personally I think you should stick with trying to get Hardy working, because at least the problem you posted in this thread would be fairly easy to solve I think; but if your computer has lots of other issues running Hardy, then maybe just live with Dapper for a while if it works. Only problem with running Dapper is if you want any help from these forums, nobody is going to be too enthused helping you sort out problems in Dapper--they will tell you to upgrade to Hardy first. ;)

---

### Post by dodle on 2008-08-16
Well, I guess I'll reinstall dapper and try the upgrade again.  'sudo apt-get dist-upgrade', right?  The last time I tried to upgrade I switched to all the Hardy repositories and entered 'sudo apt-get upgrade', which I think was the start of all my problems.

I've tried about twenty other distributions on this laptop and the only others that work are Debian and Ulteo, neither of which I was happy with.

---

### Post by caljohnsmith on 2008-08-16
I would *really* recommend downloading the Hardy CD and install that, rather than install Dapper and try to go through at least two system upgrades (I don't even remember how far back Dapper was). I think you are probably asking for alot of heartache if you want to upgrade Dapper up to Hardy, but it's your choice.

---

### Post by dodle on 2008-08-16
I've already tried that.... and given up on it.

---

### Post by dodle on 2008-08-17
Done!  It took ALL day, but I did it.  I upgraded dapper to hardy, and it was not fun.  I never want to do that again.  So, hopefully this computer never crashes.

---

