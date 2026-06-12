---
title: "Files will not delete, will dissapear, but space will still be taken"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by Capslock118 on 2006-12-15
I am moving data from NTFS to ext3 (I am moving 100% linux)

I get the data to the ext3 partition, I test it by deleting everything, and all the folders dissapears. What is weird is it never shows that it goes into the trash, yet the space is still being used up; i cant put anything else on the drive cause ive reached its max space. 

Ive unmounted, deleted that partitions and started a new but still no go.

if i use ls -la it shows that there is trash, but its not in the trash bin, so I have no way of deleting the files...what do i do here...and how can I fix this to begin with?

---

### Post by Fully216 on 2006-12-15
Have you tried deleting the file from the CLI (rm command)?

---

### Post by leech on 2006-12-16
I know what's happening here.  On the second drive, nautilus will create a .trash-<username>.  So in my case it was a .trash-leech folder.  Now all you need to do is go into that folder and delete the files, or as Fully216 said, just remove them from the terminal, though they'll be in the .trash-<username> now.

Leech

---

