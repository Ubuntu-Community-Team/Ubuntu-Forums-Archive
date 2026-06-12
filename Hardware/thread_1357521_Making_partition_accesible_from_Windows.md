---
title: "Making partition accesible from Windows"
date: 2009-12-17
forum: Hardware
---

### Post by s022038 on 2009-12-17
Hi all,
I've succesfully installed Kubuntu 9.10 on my Acer-laptop. I initially started with a windows partition and a separate ntfs partition. During the installing I formated the separate ntfs partition and divided it into a part for linux, a part for swap and finally a data part that I aimed to be accesible from both Windows and Linux. Unfortunately the latter data part is not accesible from windows and that is my current problem. 
How can undo this, i.e. how can again make the separate partition accesible for Windows?
Kristian

---

### Post by pi4r0n on 2009-12-17
None of the linux partitions will be visible in Windows. In order to see them you need to do some extra ticks in windows.

To do this see this [link]("http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html")

---

### Post by coffeecat on 2009-12-17
Have I got this right? In place of the original NTFS partition, you made three partitions: a root Linux partition (either ext3 or ext4), a swap partition and a separate data partition?

You can, as the previous poster suggests, install a 3rd party Windows driver to read an ext3 filesystem - if that is how you formatted the third partition. But there are potential problems. The explore2fs driver shown first in that link, does not list Vista as a supported version of Windows. So, if you've got Vista or W7, that will be a no go. And the Ext2IFS driver won't work at all with any ext3 partition created in the last year+ or so. That's because it can't cope with the 256-byte inodes that are now the default in ext3 partitions.

A better option (so long as you weren't thinking of using the third partition as a separate /home partition) is to format it NTFS. NTFS read/write is reliable in Ubuntu and Windows will see it as the E: or F: or whatever drive. Many forum members (including myself) use NTFS data partitions quite happily in order to share files between Ubuntu and Windows.

---

### Post by llawwehttam on 2009-12-17
The easiest way to do this is to make the data partition NTFS which windows can read and linux can as well. Is your data partition NTFS or ext 3 /ext4? If it is ext3/4 then go to System>Administration>partition editor (or similar as it changes in different releases) and reformat the data partition as NTFS. You may have to edit fstab if you want it to mount automatically in ubuntu.

---

