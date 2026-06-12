---
title: "Ubuntu 9.10 cannot see WD 500GB Ext. HDD Content"
date: 2009-11-07
forum: Hardware
---

### Post by Rinol16 on 2009-11-07
Hello ubuntuforums users!

I have a problem with viewing content of my WD 500GB External HDD. Disk os formatted in NTFS. When i plug it ubuntu mounts it succesifully, but if I open folder where HDD is mounted i see nothing. Properties says that I have 33GB free space, which is true. If i load an acronis disk director live cd, i can view contents of HDD e.g folders and files. But in ubuntu i dont see them. 

I have tried to mount disc manually with ntfs-3g, same problem. Nothing changed. 


Can somebody help me with this problem? I have a lot of content on HDD, which is very needed sometimes...

**UPD** when trying to read all content from HDD with "ls -a" command in terminal, it gives me an error "Invalid or incomplete multibyte or wide character"

---

### Post by Rinol16 on 2009-11-08
Is there any chance to even convert HDD to ext3 without losing any data?

---

### Post by tannedin on 2009-11-22
This is a quote from my fstab that I use when pmount is acting up.  
> #UUID=(vol_id) (mount point)	ntfs-3g	defaults,locale=en_US.utf8,uid=1000,gid=1000	0	0

To answer your second question, I don't know of a way to change a file partition type without needing a format which will cause a loss of data.

---

