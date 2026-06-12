---
title: "read/write problems on secondary HD"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Atlio42 on 2008-02-06
i just reformatted my secondary harddrive to ext3, but now i can only read files. when i try to change the permissions it tells me that i dont have the permission to change. is there some kind of awesome command to change it? im pretty new so i dont really know what im doing.

thanx 
Atlio

---

### Post by petersonjacob on 2008-02-06
sudo chmod 777 (then whatever the directory of the drive is)

---

### Post by banished_one on 2008-02-07
i have the same problem as Atlio42 i tried the sudo chmod777 but i think i need a little more detail since im an übernoob ^^

bnshd@desktop:~$ sudo chmod 777 /media/2
chmod: changing permissions of `/media/2': Read-only file system
bnshd@desktop:~$

i don't know what to do after this point :)

---

### Post by Yellow Pasque on 2008-02-07
What does your /etc/fstab look like? Open it with sudo gedit and try mounting with the rw option. Example:
```
/dev/sda1   /media/2   ext3  rw,auto,exec,user  0  0
```
If you're not sure of the /dev path, get it with the following commands:
```
sudo fdisk -l
sudo lshw -businfo -C disk
```

---

### Post by taurus on 2008-02-07
> **banished_one said:**
> i have the same problem as Atlio42 i tried the sudo chmod777 but i think i need a little more detail since im an übernoob ^^

bnshd@desktop:~$ sudo chmod 777 /media/2
chmod: changing permissions of `/media/2': Read-only file system
bnshd@desktop:~$

i don't know what to do after this point :)

What filesystem is it?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by banished_one on 2008-02-07
It's ntfs, is that the problem ?

---

### Post by taurus on 2008-02-07
Why don't you mount it with ntfs-3g driver so you can write to it without using sudo.

---

### Post by Atlio42 on 2008-02-07
Okay so i try chmod 777 /media/drive and i get: chmod changing permissions of media/disk  
operation not allowed. could it be the drive itslelf not mounting correctly, it used to be a dual boot, so it still starts on grub. could that be the problem? if so, what to do?

thankx

Atlio42

---

