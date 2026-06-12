---
title: "86 Ntfs"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by Gouz on 2007-11-16
Greeting everyone

I have four questions

a)what is the deference between the 86 NTFS set and 87 NTFS set when you try to format an HDD using fdisk /dev/sda

b) I formated an HDD using fdisk /dev/sda and then I followed all the instructions and it was nice formated I can read and write on it, and I see it as an NTFS.

c)When I tried to change the label I using ntfsprogs it didn't change but when I used e2label it changed 

d)when I pluged in the HDD to a windows machine the HDD was nicely shown (all three partitions) but when I tried to open one of them an error msg came up saying that I have to format the HDD because it is not formated.

Do you know the answer for any of the above?

In case you may want the output of fdisk -l:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9ac557a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10100    81128218+  86  NTFS volume set
/dev/sdb2           10101       20200    81128250   86  NTFS volume set
/dev/sdb3           20201       30401    81939532+  86  NTFS volume set


thanks 
gouz

---

