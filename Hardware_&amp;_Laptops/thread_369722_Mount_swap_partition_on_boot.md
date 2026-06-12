---
title: "Mount swap partition on boot"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by SonicTheHedgehog on 2007-02-24
How can I get my computer to mount my swap partition on boot?  On boot my swap isn't mounted and I have to type "sudo swapon /dev/sda3" to get it to mount.  How can I get it to mount on boot, automatically?

---

### Post by yabbadabbadont on 2007-02-24
Please post the contents of your /etc/fstab file.

---

### Post by SonicTheHedgehog on 2007-02-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=a9dadf24-751a-45e3-bff9-5ef3966073ff / ext2 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=96149A64149A4761 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=31315725-80f5-47e6-abde-627e8cff3627 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-02-24
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change this line

```
UUID=31315725-80f5-47e6-abde-627e8cff3627 none swap sw 0 0
```
to this.

```
/dev/sda3   none   swap   sw   0   0
```
Save it and reboot.

---

### Post by SonicTheHedgehog on 2007-02-24
YAY, now my swap is mounted on boot.  Thanks :)

---

### Post by rosieg on 2007-03-02
Yup thanks! This is one of the simplest solutions I have seen and it worked for me too...

---

### Post by ErnobmaS on 2007-07-31
Worked for me as well--thanks so much! Just out of curiosity, the other partitions in my fstab start out with a similar mess such as UUID=cd2b151b-682f-43d9-8e6c-afd20af3471e; should I change them to the more readable /dev/sda1? The other partitions seem to mount just fine, but I was wondering if it would be better (or worse) to change them--I guess what I'm really saying is I don't know what a UUID is and why it caused my swap not to mount. Anyways, thanks!

---

### Post by azwli on 2007-08-20
Hello, 

I don't know if this thread is still active, but I am having the same problem listed here but the fix isn't working.  I tried using  gksudo gedit /etc/fstab an I get this:

X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
 
So I opened the file with Konqueror and chose edit as root and changed that line, which seemed to work, but when I reboot, it changes it back to the way it was.

Any ideas?

---

