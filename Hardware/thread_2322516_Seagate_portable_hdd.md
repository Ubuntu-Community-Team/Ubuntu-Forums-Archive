---
title: "Seagate portable hdd"
date: 2016-04-28
forum: Hardware
---

### Post by Russ_Spencer on 2016-04-28
While stumbling to unsuccessfully install the upgrade (16.04), I somehow managed to wipe my backup hdd clean.  I need to reformat it so I can use it again and Seagate tells me they don't support Linux.  The told me I'd have to find out from you folks.  Any hints?  It's a Seagate FreeAgent GoFlex 500gb hdd
Thanks for your time.

---

### Post by mikewhatever on 2016-04-28
Don't think there is anything special about Seagate. Try any of the howtos, like: [http://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu](http://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu).

---

### Post by Bucky Ball on 2016-04-28
If you have an install of Ubuntu or by booting to a live session using the install media you are trying to install from, plug the drive in, open Gparted an have a look. See anything? There is a drop-down list at the top-right of the Gparted window. Can you see the external drive there? Select and format.

You will need to install Gparted if you're running a default install of Ubuntu. It's already included in the 'live' session when you're using install media.

---

### Post by weatherman2 on 2016-04-28
Not really different than formatting any other hard drive, internal or external.  Just remember that to use it with Windows again (if you need to), you need to format it as NTFS or FAT32, both of which are supported in Linux now too.  NTFS is probably the better of the two and supports very large files while FAT32 can't support large files bigger than 4.1GB.  NTFS access in Linux with the fuse driver takes a little more CPU than the other file formats.  If you doubt you'll ever use Windows again, I'd format it to ext4.

I usually use Gparted to format drives and partitions.  You can format to NTFS or FAT32.  It's easy to use.

---

### Post by Russ_Spencer on 2016-04-28
I'll give it a shot.  Thanks !!
It worked like a charm.  I like that Wikihow.  Maybe I'll see if I can get help installing 16.04. lol  Or maybe I'd better leave well enough alone. lol

---

### Post by Russ_Spencer on 2016-04-28
I followed the directions on wikihow and formatted it to FAT32.  Should I reformat to ext4?  I can't see myself ever wanting to go back to windows.

---

### Post by Bucky Ball on 2016-04-28
EXT4 it is then. But remember, you might want to use the Seagate with a Windows machine, not necessarily yours. In that case, NTFS is rule of thumb.

Glad it worked. Please mark the thread as solved to help future travelers by using Thread Tools at the top of this page. If you can't find, see second link in my thread. ;)

---

