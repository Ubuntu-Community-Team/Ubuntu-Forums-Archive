---
title: "Want to mount windows drive in Linux"
date: 2009-02-23
forum: Hardware
---

### Post by S0m3th1ngw13rd on 2009-02-23
when I type in 

```
mount /dev/sda1
```

result is: can't find /dev/sda1 in /etc/fstab or /etc/mtab

So if I use command 

```
sudo blkid
```

To get UUID and add it to fstab will that solve problem

---

### Post by konqueror7 on 2009-02-23
its better if you just added it on your /etc/fstab, so every time you boot it will mount automatically...

---

### Post by tombott on 2009-02-23
Am pretty sure you need to specify a dir to mount it in /media/disk-1 for example.
Check out my how to for auto mounting HD's

[http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10](http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10)

---

### Post by S0m3th1ngw13rd on 2009-02-23
your how to looks pretty good thank you

one question I have is will gparted work with arch

---

### Post by tombott on 2009-02-23
> **S0m3th1ngw13rd said:**
> your how to looks pretty good thank you

one question I have is will gparted work with arch

Not played with Arch yet myself, but gparted is certainly available for it:

[http://www.archlinux.org/packages/extra/i686/gparted/](http://www.archlinux.org/packages/extra/i686/gparted/)

Let me know how you get on, and thanks for the FB.

Tom.

---

### Post by S0m3th1ngw13rd on 2009-02-23
Heres my setup

Dual boot Arch and windows I can boot into either one
when I installed arch I unplugged my Windows HDD(was having trouble with loading the bootloader. After arch was installed I plugged WIN HDD back in and altered menu.lst to dual boot. My windows HDD has all my pictures, music, and documents that I want to transfer to my Linux side.  Will using gparted allow me to add a mount point to Win HDD without messing up my win installation(its my gaming console so to speak). 

Here is result of    

sudo blkid:
```
/dev/sda1: UUID="127CCA8A7CCA67D5" LABEL="win_xp_pro" TYPE="ntfs" 
/dev/sdb1: UUID="23ec470f-6d48-47d8-95e2-5aaf96143ac6" TYPE="ext2" 
/dev/sdb2: TYPE="swap" UUID="84cd78c6-6740-4567-bab6-462f77bf84bb" 
/dev/sdb3: UUID="c8b50b64-f8f7-42c8-abfb-b29f5dcdc46f" TYPE="ext4" 
/dev/sdb4: UUID="8921e90a-219a-4085-9933-4b3bad1177e4" TYPE="ext4"
```

and fstab file:
```
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

UUID=23ec470f-6d48-47d8-95e2-5aaf96143ac6 /boot ext2 defaults 0 1
UUID=84cd78c6-6740-4567-bab6-462f77bf84bb swap swap defaults 0 0
UUID=8921e90a-219a-4085-9933-4b3bad1177e4 /home ext4 defaults 0 1
UUID=c8b50b64-f8f7-42c8-abfb-b29f5dcdc46f / ext4 defaults 0 1
```

I would like to mount win drive at boot so I have a little place to store a few things, there is a bit of space left over there.

---

### Post by taurus on 2009-02-23
You should consider mounting / first before you mount the others (/boot & /home) in /etc/fstab.

```
UUID=c8b50b64-f8f7-42c8-abfb-b29f5dcdc46f / ext4 defaults 0 1
```

---

### Post by S0m3th1ngw13rd on 2009-02-23
> **taurus said:**
> You should consider mounting / first before you mount the others (/boot & /home) in /etc/fstab.

```
UUID=c8b50b64-f8f7-42c8-abfb-b29f5dcdc46f / ext4 defaults 0 1
```

So the order they are listed in /etc/fstab is the order they are mounted?
I did not know that but I will change the order. Thank you

---

### Post by stchman on 2009-02-23
> **S0m3th1ngw13rd said:**
> when I type in 

```
mount /dev/sda1
```

result is: can't find /dev/sda1 in /etc/fstab or /etc/mtab

So if I use command 

```
sudo blkid
```

To get UUID and add it to fstab will that solve problem

If the WIndows drive is NTFS then installing ntfs-config will do what you want.

```
sudo apt-get install ntfs-config
```

Only think is that you enable write support and write support on the C:\ drive I do not recommend.  You can delete something important and not get it back.  I recommend if you need access to the C:\ drive to do it via read only with the ro switch in the fstab.

Example
```
/dev/<ntfs drive>   <mount point> ntfs  auto,defaults,ro  0   0
```

Hope this helps.

---

