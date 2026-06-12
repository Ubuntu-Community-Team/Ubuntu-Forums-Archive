---
title: "Nautilus will not let me change permissions of external hard drive"
date: 2014-06-03
forum: Hardware
---

### Post by ewangr on 2014-06-03
Just installed 14.04, and it automounted my 9TB external USB3 drive. So far so good. But when I right click the drive in Nautilus to select Properties, and then choose permissions it shows that the owner (me) has read-write. It shows the group having none and others having none. If I try to change the group or others it flashes, and then stays where it originally was. How do I change these?

---

### Post by sudodus on 2014-06-03
It might be the problem with Windows file systems (FAT32 and NTFS), that the permissions will be set when mounted, and cannot be changed afterwards. In that case there are two solutions

1. Unmount and remount with the permissions you prefer (and do it automatically in the future if you wish).

2. Change the file system to a linux file system, for example ext4. Then you can change permissions of directories and files like in the internal drive.

---

