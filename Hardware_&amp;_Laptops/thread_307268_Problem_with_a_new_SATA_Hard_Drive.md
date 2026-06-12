---
title: "Problem with a new SATA Hard Drive"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by Zaff on 2006-11-26
Hi.
Here's the situation : I'm using dapper drake and I just bought a new Western Digital Disk SATA II 400Go. I made two partitions on it through nidows, one in Fat 32 and the other as ext 3 and it seemed to work fine. however when i try to mount it through ubuntu here's what I get :
```
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
mount: wrong fs type, bad option, bad superblock on /dev/sda6,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

```
I went through the fstab and added the following :
```

/dev/sda5	/media/lee	ext3	defaults,users,nls=utf8,umask=007,gid=46 0       1
/dev/sda6	/media/big-fat	vfat	defaults,users,nls=utf8,umask=007,gid=46 0       1

```
still not working, except when I use sudo like so :
```
sudo mount -t ext3 /dev/sda5 /media/lee
```
But I can only write on the drive using sudo and i'd like to be able to use nautilus with a normal user.
Thanks for any kind of help. I was also wondering if maybe there was an update for the sata drivers and if so how to get it ?What's the name of the packet.
Thanks

---

### Post by taurus on 2006-11-26
Try changing those two lines to

```

/dev/sda5  /media/lee  ext3  defaults  0  1
/dev/sda6  /media/big-fat  vfat	 iocharset=utf8,umask=000  0  0

```
Save it and reboot...

---

