---
title: "maxtor onetouch 4 mini wont work"
date: 2008-08-28
forum: General Help
---

### Post by tercelkisor on 2008-08-28
it worked before i installed ubuntu but now it dosnt work on windows or ubuntu.

it works on my moms laptop tho..

i read about this thing

sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force

but what i get is this

$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/hd-ntfs: No such file or directory

i would appreciate any help...

---

### Post by mssever on 2008-08-28
Mount and cleanly unmount it twice on a Windows machine, then it should work.

---

### Post by tercelkisor on 2008-08-28
thanks ill try

---

### Post by tercelkisor on 2008-08-28
it didnt work.. should i try and restart my cpu with it connected or is there another trick i could use?

---

### Post by mssever on 2008-08-29
I just re-read your original post.> **tercelkisor said:**
> it worked before i installed ubuntu but now it dosnt work on windows or ubuntu.Same machine? Sounds like a hardware problem.
> fuse: failed to access mountpoint /media/hd-ntfs: No such file or directory
Does /media/hd-ntfs exist?

---

### Post by tercelkisor on 2008-08-29
idk about all that stuff... all i know is that it works on my moms comp and  before ubuntu install but now it dosnt do anything when i connect it

---

### Post by mssever on 2008-08-29
If you want help, you need to answer the questions asked, rather than dismissing them. Saying that it worked before but not now doesn't get you any closer to an answer.

---

### Post by Ms_Angel_D on 2008-08-29
Open computer from the places menu then under filesystem >> Media  see if there is a folder called hd-ntfs if not you'll have to creat it.

Open the terminal from the menu (Applications >> Accessories >> Terminal) and enter the following

```
sudo mkdir /media/hd-ntfs
```

that was all mssever was trying to see is if the folder existed.

---

### Post by tercelkisor on 2008-08-29
i have that folder..

nothing is in it tho..  should there be something in it?

---

### Post by Ms_Angel_D on 2008-08-29
first make sure your drive is plugged in

(I'm not positive if this will work but it's worth a shot)
in the terminal

```
sudo gedit /etc/fstab
```

in the fstab file locate ntfs-3g  and change it to ntfs  then save the file and then in the terminal 

```
sudo mount -a
```
and see if that works.

---

### Post by tercelkisor on 2008-08-29
this is what i get > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=8d99629b-b00d-4cfe-9d0b-950a9d70ac97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=915e2f76-74e0-483e-9a99-834b2aade1a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

idk.

---

