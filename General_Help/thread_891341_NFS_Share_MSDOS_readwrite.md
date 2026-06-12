---
title: "NFS Share MSDOS read/write"
date: 2008-08-16
forum: General Help
---

### Post by Sam Lars on 2008-08-16
I'm using 8.04 on the server and clients.
I have an external drive mounting from fstab.
```
/dev/sde1 /500 msdos defaults 0 1
```
I'm exporting it with NFS with the same options that I am using for my ext3 mount points that work fine.
```
/500            192.168.1.1/24(rw,async,no_subtree_check)
```
I have opened up the permissions on the mount point, but as soon as it's mounted, they change.  I've tried different squash options for exports and specifying uid/gid in fstab.  I still can't get an NFS client to write to the share.
The working shares show on the clients that all directories are owned by the local user.  /500 shows them as owned by root.
I'm thinking this has something to do with the fact that it's msdos (fat32) filesystem.  Would it seriously be better just to reformat it?  Or is that not the problem?
Thanks.

---

### Post by scarf on 2008-12-17
i am also getting permission denied, and i can't see anything hopeful about sharing an ms-dos / fat32 / vfat partition with nfs.  reformatting to ext3 isn't really an option, as this is an external drive that is moved between different OS's.

so, if there is any way to get NFS working nicely with this type of partition/filesystem, i am eagerly awaiting....

---

### Post by fragos on 2008-12-17
FAT doesn't support permissions and ownership like Linux does. FAT drives external to the box on USB, Firewire and External SATA connections can be mounted directly but NFS only applies to networked drives on other Linux boxes. Networked drives on Windows boxes use Samaba.

---

### Post by scarf on 2008-12-17
thanks. so i guess it's impossible for now, unfortunately.

i'll just setup samba.

---

