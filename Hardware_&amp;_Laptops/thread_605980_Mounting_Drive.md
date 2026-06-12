---
title: "Mounting Drive"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Phoros42 on 2007-11-07
Good Afternoon,

I would like some help mounting my drive.

It used to be an ntfs partition but I could not access the data due to something about an unclean shut-down. After deciding that the contents of the drive were not needed I made an ext3 partition using g parted.

I've only installed Ubuntu Gutsy yesterday and have little experience with Linux. Although I am competent enough to use the terminal, even if I don't know what every command does exactly. 

I am not asking to be spoon-fed but simply pointed in the right direction. Thank you

best regards,
Phoros

---

### Post by taurus on 2007-11-07
_Assuming_ that partition is **/dev/sdb1**, edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

If not sure which partition it is, look at the output of this command from a terminal.

```
sudo fdisk -l  <-- lower case letter l, not number 1
```

---

