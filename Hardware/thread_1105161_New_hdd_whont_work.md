---
title: "New hdd whont work"
date: 2009-03-24
forum: Hardware
---

### Post by maclin on 2009-03-24
i just put in a new 80 gb Hdd and i formated it but i have to be the root to right/read
how do i give my account root access or activate the root user

---

### Post by plucky on 2009-03-24
Checkout the [Psychocats Mount Linux Tutorial](http://www.psychocats.net/ubuntu/mountlinux) assuming the new hard drive is using an ext3 partition.


Good luck
;)

---

### Post by albandy on 2009-03-24
this is the correct way the disk should work, a user should not be able to write in a disk whithout the admin authorization.

for example, create a folder
sudo mkdir /mynewdisk/myfolder
then change the owner of the folder
sudo chown user:group /mynewdisk/myfolder

now you're able to write in /mynewdisk/myfolder

---

