---
title: "How To:  Move &quot;/home&quot; Partition onto the Main Ubuntu Partition"
date: 2010-06-18
forum: Hardware
---

### Post by u2rcrazy on 2010-06-18
How can I move the "/home" Partition onto the Main Ubuntu Partition?  See screenshot below

[ATTACH]160865[/ATTACH]


I tried to unmount the /home drive but I received this error message:

[ATTACH]160864[/ATTACH]

FYI:  My objective is to change the **ext4** partition to and **NTFS** partition so that Windows and Ubuntu can read and write to it.  Thanks for any input you have):P

Sincerely,
Bob:guitar:

---

### Post by oldfred on 2010-06-18
If I remember correctly, you can edit fstab to remove the /home mount and it will automatically create a new /home inside your install when you reboot. Then you can just use cp -a oldhome  newhome to copy with attributes everything into your new home. Be sure to inculde the -a parameter as you want all the ownership and permissions from your old home copied also.

It is just the opposite of 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

