---
title: "Rename partitions so same name in Nautilus, Partition Editor and all O/S ?"
date: 2008-10-11
forum: General Help
---

### Post by Browser_ice on 2008-10-11
I have a multi-boot system and I had originally created backup partitions for each O/S on the 2nd HD. But as I did not wrote them down and started to use some, I am finding myself in the situation where I do not remember which one is which through Nautilus, Gnome Partition Editor and through any O/S.

How can I rename those partitions so they have the same name no matter from where I look at them ?

---

### Post by jerome1232 on 2008-10-11
Just change their labels, if you want to do that in Ubuntu then you need a few programs to do so.

```
mtools           - Fat12,16,32
ntfsprogs        - ntfs
e2fsprogs        - ext2,ext3
jfsutils         - jfs
reiserfsprogs    - reiserfs
xfsprogs         - xfs
gparted          - a gui partition editor
```

You need to Unmount the file system, right click the partition and select Label (note make sure your not using device->DiskLabel as this will erase anything on the drive, it will warn you about it though.)

If you are wanting to do this to your root and home then you obviously will need the live cd to do so.

---

### Post by Browser_ice on 2008-10-11
> **jerome1232 said:**
> Just change their labels, if you want to do that in Ubuntu then you need a few programs to do so.

```
mtools           - Fat12,16,32
ntfsprogs        - ntfs
e2fsprogs        - ext2,ext3
jfsutils         - jfs
reiserfsprogs    - reiserfs
xfsprogs         - xfs
gparted          - a gui partition editor
```

You need to Unmount the file system, right click the partition and select Label (note make sure your not using device->DiskLabel as this will erase anything on the drive, it will warn you about it though.)

If you are wanting to do this to your root and home then you obviously will need the live cd to do so.

Sorry re-wrote reply.
In Qparted, when I right click, I do not see the option Label.

---

### Post by jerome1232 on 2008-10-11
Yeah ***don't*** select disklabel

See my screenshot for an example

---

### Post by Browser_ice on 2008-10-11
> **jerome1232 said:**
> Yeah ***don't*** select disklabel

See my screenshot for an example



I am doing the right thing, but LABEL just is not in the right click menu.

---

### Post by jerome1232 on 2008-10-11
It's unmounted right?

Well barring that, you can do it from the command line, this guide tell's you how to do it for every type of file system

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Browser_ice on 2008-10-11
> **jerome1232 said:**
> It's unmounted right?

Well barring that, you can do it from the command line, this guide tell's you how to do it for every type of file system

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Mounted or unmounted, the LABEL option does not appear in the right click menu.

In any case, I'll check the link. Thx

---

