---
title: "External Hard Drive Partioning Permissions glitch"
date: 2008-12-21
forum: Hardware
---

### Post by brucem91 on 2008-12-21
Hello. I have a 320 gb external harddrive, and using gparted, I partitioned a section of it to be ext3, for storing larger than 4 gb files. In ubuntu, I can only read the ext3 partition, I cannot write changes to it unless I use "sudo nautilus" from the terminal. I would like to be able to read and write to it as a normal user. I opened gparted, but I didnt see anything about permissions. The other fat32 partition works just fine, just not the ext3 one. 
Thanks
Bruce

---

### Post by logos34 on 2008-12-22
You just need to edit ownership and permissions:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(-> bottom)

---

