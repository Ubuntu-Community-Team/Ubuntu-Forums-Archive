---
title: "[SOLVED] Reformat External Hard Drive"
date: 2008-07-24
forum: Hardware
---

### Post by jkyahoo101 on 2008-07-24
Ok I need to reformat my external hd to get rid of Ubuntu that I tried to install to it. Instead I installed Ubuntu 8.04 through Wubi or whatever it is. Now I am not sure how to reformat it and I also want it in a format so Windows XP and Ubuntu can recognize and store things on it. I have a lot of music so I want to be able to access it in XP and Ubuntu.

---

### Post by coffeecat on 2008-07-24
The best choice would be to format it with the NTFS filesystem. Either install Gparted in Ubuntu or you can use Windows - somewhere in the Control Panel, but I can't remember where.

---

### Post by jkyahoo101 on 2008-07-24
If it is built into XP then I might as well use it. Plus that is where all of my files are.

---

### Post by coffeecat on 2008-07-24
Here you go. I've rebooted into Windows - just for you. :wink:

Control centre > Administrative Tools > Computer Management > Disk Management. You can right-click on a disc/partition and format. You can usually reformat from My Computer by right-clicking on the appropriate icon, but as the drive is formatted with a Linux filesystem, you might not be able to do this. But you will be able to in Computer Management. A Linux partition does show up even though Windows doesn't understand it.

By the way, the reason I suggested NTFS is that Ubuntu 8.04 can read and write reliably to NTFS. Much less fiddly than installing Windows drivers for Ext3, and probably more reliable. The older FAT32 filesystem would do, but you're limited to 4Gb sized files.

---

### Post by jkyahoo101 on 2008-07-24
Thank you very much. Now it shows what the Ubuntu install is taking and the free space. Can I just delete the logical drive under the Ubuntu partition?

---

### Post by jkyahoo101 on 2008-07-24
Ok I deleted that partition Ubuntu was taking up and I am making a new one with Windows but it is taking FOREVER. I think I will use a different program or something. It also is only displaying 465 total GB when I know it is 500Gb. How do I get that space back?

---

### Post by jkyahoo101 on 2008-07-24
Never mind I was being stupid. I just remembered that factory marked sizes and real sizes are different.

---

