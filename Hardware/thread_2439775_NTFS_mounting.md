---
title: "NTFS mounting"
date: 2020-04-01
forum: Hardware
---

### Post by asai on 2020-04-01
Hi,

I have a HDD that I dismantled from a PC. This one has a lot of data and has NTFS. I have inserted it into my Ubuntu server, but am struggling that when the file system is mounted it is read-only. How can I fix this? An alternative is to copy all data to another disk and format with ext4, but don't feel like it.

The server is 18.04

Heres my line in fstab:
```
UUID=184C1EDD4C1EB60A /mnt/ntfs/ ntfs-3g  rw 0 0
```

---

### Post by yancek on 2020-04-01
You have the proprietary microsoft windows ntfs filesystem on the drive partition.  Why not use windows to access the data?  I'm not sure what your intentions are.  The filesystem being read-only should still allow you to access it and copy data FROM that partition.  If you are wanting to use the drive in Ubuntu, you will need ntfs-3g installed.  I don't use the server version so I' m not sure it is available.  You should be able to check with the command below:

> which ntfs-3g

If installed, you should see:  /bin/ntfs-3g

Can you access and write to the filesystem using root permissions (sudo)?

---

### Post by asai on 2020-04-01
Hi,
Thanks for your reply.
The command shows /bin/ntfs-3g
I have only read access, even when using sudo. :(

---

### Post by TheFu on 2020-04-01
Two things.

If the file system wasn't correctly, properly, closed by Windows, then there is no way to make it read-write.

2nd thing, because NTFS is a foreign file system, permissions for the entire file system - directories and files - are set through mount options. No other way.  You probably need more complex mount options for the fstab entry. These forums are full of examples. Search for "NTFS big_writes" to find some of those threads with examples.

---

### Post by asai on 2020-04-02
Solved it.

Heres my new line in fstab:
```
UUID=184C1EDD4C1EB60A /mnt/ntfs/ ntfs-3g  auto,umask=000,utf8  0  0
```

---

### Post by TheFu on 2020-04-02
> **asai said:**
> Solved it.

Heres my new line in fstab:
```
UUID=184C1EDD4C1EB60A /mnt/ntfs/ ntfs-3g  auto,umask=000,utf8  0  0
```

That seems like a poor fstab line.

[LIST]
[*]For portable devices, I find using a LABEL= instead of UUID= to mount lets me have clearer understand of the actual storage being mounted. 
[*]umask should probably be 002 for security
[*]the big_writes option should improve performance by 30% or more.
[*]Since all permissions and ownership are controlled at mount time for NTFS/FAT-whatever storage, usually a specific userid and groupid are selected to allow the owner and group to be correct set for the specific partition.
[/LIST]

Options that I use for NTFS mounts:
```
nodev,nosuid,noatime,windows_names,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```
The nodev/nosuid are for security.
Noatime is for a little speed. It is very common on all storage types.
windows_names prevents creation of names that won't work for Windows.
async,big_writes are for performance
timeout is to prevent missing or bad cables from filling the system logs with failures.
Sometimes I need directories and files to have different default masks, hence fmask/dmask. umask is fine.
uid/gid is because my storage is used only by my account.  Other userids would need different values for their storage. Use the 'id' command to see the values needed.

An fstab line cannot be continued onto another line, but must all be one line.

---

### Post by Morbius1 on 2020-04-02
> **asai said:**
> Solved it.

Heres my new line in fstab:
```
UUID=184C1EDD4C1EB60A /mnt/ntfs/ ntfs-3g  auto,umask=000,utf8  0  0
```
Curious.

Your original fstab declaration was this:
> UUID=184C1EDD4C1EB60A /mnt/ntfs/ ntfs-3g  rw 0 0
Permissions wise those two are equivalent.

An ntfs partition defined in fstab - unless otherwise specified by selecting other options - will always mount with 777 permissions.

I took an ntfs partition and changed the options to your original:
> UUID=40F76A4E40B0C5CB /DataN/   ntfs-3g rw 0 0
It's permissions are 777:
> tester@vub1804:~$ ls -dl /DataN
drwxrwxrwx 1 root root 4096 Oct  8  2017 /DataN
Technically your umask is redundant:

> umask=value
              Set the  bitmask of the file and directory permissions that  are
              not present. The value is given in octal. [COLOR=#0000cd]The default value is 0
              which means full access to everybody.[/COLOR]

Are you sure you didn't take an intermediate step somewhere like the one suggested by TheFu:
>  If the file system wasn't correctly, properly, closed by Windows, then there is no way to make it read-write.

---

