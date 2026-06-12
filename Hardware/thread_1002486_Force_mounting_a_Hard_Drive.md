---
title: "Force mounting a Hard Drive"
date: 2008-12-05
forum: Hardware
---

### Post by Godleflopest on 2008-12-05
Ubuntu can't mount my hard drive and tells me to force mount it, I use the script it says and apparently only the root can do it.
What am I doing wrong?

---

### Post by pluckypigeon on 2008-12-05
> **Godleflopest said:**
> Ubuntu can't mount my hard drive and tells me to force mount it, I use the script it says and apparently only the root can do it.
What am I doing wrong?

type: 

```
sudo
```

in front of the command

---

### Post by taurus on 2008-12-05
Are you trying to mount a ntfs partition/drive?  You could try something like these from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/widows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
df -h
```
_Assuming_ /dev/sda1 is the one you want to mount.

Otherwise, run this command from a terminal and post the output here.

```
sudo fdisk -l
```

---

### Post by Godleflopest on 2008-12-06
Yep, that did it. Thanks guys.

---

