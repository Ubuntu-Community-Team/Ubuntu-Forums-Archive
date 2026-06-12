---
title: "PC crash and drive wont mount"
date: 2014-02-02
forum: Hardware
---

### Post by spook42088 on 2014-02-02
k so when i turned my PC on this morning it booted up fine,  did a few updates, restarted the PC and could no longer use my mefia hard drive
OS. linux mint 16

when i try to open the drive i gfet this

Error mounting system-managed device /dev/sda1: Command-line `mount "/mnt/BB16-7778"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

never had a problem like this till today.
any ideas?

---

### Post by Bashing-om on 2014-02-03
spook42088; Hi !

This:
> 
 mount: wrong fs type, bad option, bad superblock on /dev/sda1,

Says there may be a more serious problem, but, let's see if  the check/repair file system utility gives any joy:
Boot the live cd - as any file system checks must be done when the file system in question is not mounted; -> "try ubuntu" mode ->
activate a terminal:
terminal codes:
```

sudo fdisk -lu ##for legacy partitioning schemes, else  use gdisk##
sudo parted -l
sudo parted /dev/sda unit s print

```
As we want to be absolutely sure that sda1 is formatted as ext4, and also contains the '/' directory.

Good to go as sda1 is what we are working on ? Then:
Run the file system checks from that liveMedium.
```

##e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required##
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck##
sudo e2fsck -f -y -v /dev/sda1

```

If you are not comfortable, or do not fully understand what these commands do, ask for amplifying info and show us the output of the 1st set of commands. We can do this s l o w l y and carefully.
Good possibility that this will resolve the situation, but also possible will have to delve in deeper.

[INDENT][INDENT]it is ubuntu
[INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT]

---

