---
title: "Hard disk partition recommendation ubuntu desktop 11.4 x64"
date: 2011-07-24
forum: Hardware
---

### Post by tasmanian_devil on 2011-07-24
Hi all,
i have IBM SL510 with 320GB Hard Disk and 4GB RAM memory. 

I need suggestion for disk partitions, how many partition and which size. 
Do I need LVM or not ? 

I will use only ubuntu OS on this laptop. 


Thanks

---

### Post by oldfred on 2011-07-24
Some like LVM as it gives flexibility on partitions if you want to change or move around. But it adds a level of complexity and you have to use different LVM tools to edit & update partitions.

If you are sure you are not ever using windows on this drive I would use gpt not MBR for partitioning. You can use gpt inside the LVM if you want also. GPT will be the future, but is not now required unless your drive is over 2TiB. I have it on my 160GB drive booting Maverick.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

Are you planning on experimenting with other installs?, have lots of data requirements or any other future needs. It often is difficult to plan ahead, but that effects partition planning (part of advantage of LVM, but I do not want the extra level of complexity, so I try to plan the best I can). I left some space unallocated for future use as new drive gave me lots of room to work with.

---

