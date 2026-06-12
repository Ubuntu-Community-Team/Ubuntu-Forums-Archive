---
title: "Can't Delete folders on an NTFS mount"
date: 2009-09-11
forum: Hardware
---

### Post by krackersk on 2009-09-11
Hi,

I have mounted my windows vista NTFS harddrive using fstab but I can't deleted existing folders! I can delete existing files, I can also delete folders I create on the NTFS drive in linux. This doesn't work in either my user account or root.

My fstab is:

#Mount the windows drive at startup
/dev/sda3    /mnt/windows    ntfs-3g    defaults,locale=en_AU.utf8    0    0

"mount -l" gives

/dev/sda3 on /mnt/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [OS]

Any suggestions on getting this working?

---

### Post by laluz on 2009-09-12
could you post the output of 
ls -al /pathToYourFolder

---

### Post by krackersk on 2009-09-12
Sure, I'm trying to delete the "My Documents" folder

ls -al of its parent folder gives (only copied the relevent line as it is quite long)

drwxrwxrwx 1 root root       0 2009-09-04 11:15 My Documents

ls -al of "My Documents" gives

ls -al "/mnt/windows/Users/angus/My Documents"

total 8
drwxrwxrwx 1 root root    0 2009-09-04 11:15 .
drwxrwxrwx 1 root root 8192 2009-09-12 12:09 ..

When I try to delete the folder

sudo rmdir "/mnt/windows/Users/angus/My Documents"

the error I get is:

rmdir: failed to remove `/mnt/windows/Users/angus/My Documents': Operation not supported

---

### Post by JHan816 on 2009-09-12
Spaces in filenames and directory names cause problems.
 
Try:
 
**sudo rmdir "/mnt/windows/Users/angus/My\Documents**
 
Add a \ in place of the space.
 
I had trouble with this on my samba shares too. 
 
 
Just an idea, I am new to this Linux stuff...
 
--John

---

### Post by krackersk on 2009-09-12
I tried the "\" but this didn't work.
I also tried to delete:

sudo rmdir /mnt/windows/Users/angus/Recent

and this gives:

rmdir: failed to remove `Recent': Operation not supported

So it is not to do with spaces.

Is it something to do with vista as this folders where came with the vista machine preinstalled. I'm running dual boot at the moment as I have to use windows at work

---

### Post by falconindy on 2009-09-12
Tried it with sudo? It's being mounted by root, not yourself, so permissions could be an issue.

---

### Post by JHan816 on 2009-09-13
Sorry the \ trick did not work...
 
I think ownership for ntfs is determined when mounting using the uid=user_name or gid=group_name in fstab.
 
Permissions are set by umask=000 for permission of 777 for example.
 
I am trying to figure out this stuff too...

---

### Post by spoon_ on 2009-11-09
I'm having the same problem! The My Documents folder is protected somehow. But I want to write to it. Anyone find a solution yet?

Thanks.

EDIT: ooh I get it, My Documents isn't a real folder. It's some kinda fancy windows virtual folder. The real one is called Documents. I've been out of the windows game too long...

---

