---
title: "Getting &quot;E297: Write error in swap file&quot; error!"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by senthilums on 2009-08-06
Dear All,

I am new to Linux, I have installed Ubuntu in my laptop wich has windows Vista OS.

Error:
When I try to create new file in my home directory, I am getting the error - E297 and E303.
I guess no space left in my home directory to create or write any files in my home directory.

Note:
While installing the Ubuntu, I have exported the Windows Documents, so I believe it has occupied the whole space in this partition(18.5 GB).

Help me how to unmount the windows documents and make use of the memory allocated for Ubuntu.

When I run the df command in my terminal it gives-

File system    1k-blocks      Used            Available      Use%         Mounted On
/dev/sda7       18239964      17379588     0                  100%         /


Thank You,
Senthil

---

### Post by Partyboi2 on 2009-08-07
Hi, if you have free space on the partition that windows is, you can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) and shrink down you windows partition and increase the size of the Ubuntu partition, using the resize function.
Remember to backup your important stuff before working on partitions.

---

