---
title: "new hdd cannot access wont give me permission"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by larryweeks on 2008-01-05
I have installed a  new 250 gig hdd (sata) which is working and i have setup, it is supposedly formatted although I cannot put anything on it. It says I dont have permission.
I am currently the only user on the machine.

what do I do?

---

### Post by taurus on 2008-01-05
What filesystem is that new harddrive:  fat32, ntfs, or ext3?

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by larryweeks on 2008-01-05
it allowed me to make an ext 2 disk, which i partitioned into 2 making the first ext 3 and the second as swap
I can read the disk in the file manager but cannot put anything on it as it says i do not have permission ...i am using the 7.10 gutsy gibbon in 64 bit 
It seems to say that to me in a lot of areas but I havent got that figured out yet.. not to mention my desktop will not load a background and remains black

llarry

---

### Post by taurus on 2008-01-05
Where do you mount it?  You just need to change the ownership of that mount point from root to your login name.  Then, you can write to it anything you want.

```
cat /etc/fstab
mount
```

---

### Post by larryweeks on 2008-01-05
i tried the command all it did was remount the drive I still cannot get in. The drive is in media/mynewdrive

---

### Post by taurus on 2008-01-05
Do you mount it through /etc/fstab?

_Assuming_ your login name is **larry**, try

```
sudo chown -R **larry**:**larry** /media/mynewdrive
sudo chmod -R 755 /media/mynewdrive
ls -la /media
```

---

### Post by DJ_Peng on 2008-01-05
> **taurus said:**
> _Assuming_ your login name is **larry**, try

```
sudo chown -R **larry**:**larry** /media/mynewdrive
sudo chmod -R 755 /media/mynewdrive
ls -la /media
```

This needs to get stickied someplace where it can be found easily. I kicked WinXP from my comp recently and had to reformat a partition from FAT32 to ext3. If this had been handier it would have made my life a lot easier during the change.

---

