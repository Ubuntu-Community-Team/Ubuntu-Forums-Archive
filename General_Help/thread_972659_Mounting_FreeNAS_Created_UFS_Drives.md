---
title: "Mounting FreeNAS Created UFS Drives"
date: 2008-11-06
forum: General Help
---

### Post by sesh_00 on 2008-11-06
G'day All,

I'm having a little bit of trouble mounting a pair of FreeNAS created UFS drives on a fresh install of Ubuntu Server. Here's where I'm at:

```

sesh@ubuntu-server:~$ sudo mount -t ufs -o ufstype=44bsd /dev/sdb1 ~/disk1 -r
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sesh@ubuntu-server:~$ dmesg | tail
...
[ 1038.124285] ufs_read_super: bad magic number

```

I'm attempting to mount read only, and I realise that to mount it with write access I need to recompile the kernel with that switch. Happy to do that later, but for now just reading the disk would be nice.

Any suggestions? It doesn't work without specifying the filesystem type, or without the "ufstype=44bsd" either.

---

