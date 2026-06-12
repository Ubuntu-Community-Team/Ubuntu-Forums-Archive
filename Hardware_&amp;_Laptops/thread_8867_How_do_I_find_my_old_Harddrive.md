---
title: "How do I find my old Harddrive?"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by Swehulk on 2004-12-21
I just installed Ubunto and dont know how to find my secondery HD, It's in ntfs but I shloud still be able to read from it right?:)

---

### Post by jabbo on 2004-12-21
You have to mount it.
For example, if you want to want to mount the first partition on your secondary HD to /home/username/myntfsdisk, create that directory and type ```
mount /dev/hdb1 /home/username/myntfsdisk
``` in a terminal. Then you'll find the contents of that partition in that directory. Check ```
man mount
``` for additional information.
Don't know if there are any ntfs-specific issues to be aware of, though.

CU
jabbo

---

### Post by Swehulk on 2004-12-22
Thanks jabbo

but nothing appears in thet folder.

for the record I can say that my 2:nd HD is a single partision one

---

### Post by Swehulk on 2004-12-22
OK I have come alittle further on the way now it says that I dont have permision :???:

---

### Post by Swehulk on 2004-12-22
it says : You do not have the permissions necessary to view the contents of "myntfsdisk".

any sugestions?=)

---

