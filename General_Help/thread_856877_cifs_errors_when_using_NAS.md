---
title: "cifs errors when using NAS"
date: 2008-07-11
forum: General Help
---

### Post by tramir on 2008-07-11
I have the following problem that I can't really explain (and solve). I mount a samba share on a NAS device:

```
mount.cifs //192.168.0.200/Backup /media/home_backup -o guest,rw,nounix,uid=mircea,gid=mircea,file_mode=0777,dir_mode=0777
```

I can copy/delete/do whatever I want to it without any problem. 

Next, I create a file, assign it to a loopback device, and create an lvm volume inside and mount it. It all works fine. But: when I try to copy something inside this volume, I get a whole bunch of errors, starting with:

```
CIFS VFS: Send error in read = -5
---many identical errors skipped---
CIFS VFS: Send error in read = -5
Aborting journal on device dm-0.
__journal_remove_journal_head: freeing b_frozen_data
__journal_remove_journal_head: freeing b_frozen_data
__journal_remove_journal_head: freeing b_frozen_data
__journal_remove_journal_head: freeing b_committed_data
__journal_remove_journal_head: freeing b_frozen_data
ext3_abort called.
EXT3-fs error (device dm-0): ext3_journal_start_sb: Detected aborted journal
Remounting filesystem read-only
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: No response to cmd 47 mid 13228
CIFS VFS: Write2 ret -11, wrote 0
CIFS VFS: Write2 ret -11, wrote 0
CIFS VFS: Write2 ret -28, wrote 0
....
```

I can guess that the "write2 errors" are due to the fact that the disk is remounted as read-only. I don't understand how it gets to that point: the send error and the aborting of the journal. Does anybody have any clue about this? What to do about it? Are there any options to mount CIFS shares that could help (I've tried a whole bunch until now, like forcedirectio, noacl, wsize=4096, nothing helped)? Any suggestion is greatly appreciated.

---

### Post by tramir on 2008-07-12
Does anybody have any clue what could cause those read errors? And, more importantly, if there's any way to deal with them?

---

### Post by tramir on 2008-07-13
I did some more tests. I get the same problem in the following cases:

1. create a file on the NAS, create a file system within that file and then mount it as a loop device; copy something on this file system

2. create a VMWare disk on the NAS, mount it outside a virtual machine using vmware-mount; copy something on this disk

3. as I mentioned above, create a bunch of files on the NAS, combine them in an LVM, create a file system on the LVM; copy something on this file system

Again, the NAS works perfectly fine if I just copy directly to it, rather than to a filesystem-within-a-file. Is there something special about these 3 methods above? Do they require some sort of "disk-level access" that simply doesn't work via CIFS? Is there any option when mounting a CIFS/SMBFS share that would enable this kind of access?

---

### Post by tramir on 2008-07-14
Even more tests. Scenarios 1 and 3 above also fail with a USB hard disk, formatted as NTFS, though I'm not sure that would make a difference. I already uninstalled VMWare, so I can't test the virtual disk scenario. This makes me think that there's something about loopback files and how they're being accessed that just makes these things work on local drives but not on "remote" drives, where I include USB mounted ones as well. Or is it because they're on non-native filesystems, fat or ntfs? Does anybody know anything about this?

---

