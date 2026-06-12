---
title: "USB harddrive sharing"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by swear on 2008-01-23
Hello,


I've just started using an old laptop as a fileserver/backuplaptop and I've installed ubuntu desktop on it.

Most of the files I want shared via this computer are on external USB harddrives, and as I plug them in they work great with the main user, but I can't seem to remotely access the files with any other user, like via SSH or SFTP.

Seeing as these harddrives are FAT32 they don't support chmod anyway. 

How can I make them shareable?


Cheers

:popcorn:

---

### Post by chrisdeckard on 2008-01-24
If security isn't an issue, you could try mounting the device with mode=0777, which will make all the files rwx for all users.

You might look also look at your Samba config if you're using Samba.

-Chris

---

