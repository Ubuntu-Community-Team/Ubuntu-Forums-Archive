---
title: "[SOLVED] Mounting on statup"
date: 2008-11-16
forum: General Help
---

### Post by Comzee on 2008-11-16
I have a second hard-drive in my PC that wont auto mount on startup. I know I have to edit my fstab file but I dont know exactly how to do it.

my out for sudo fdisk -l is:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012572

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

```

My output for cat /etc/fstab is: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=be315416-5634-4213-80a6-23613c92e8c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=816a70b6-4549-4eb5-abe2-3f69fc0e3b49 none            swap    

```

Can somebody give me a way to auto-mount this?

Thanks in advance

---

### Post by taurus on 2008-11-16
Where do you want to mount /dev/sdb1?  For now, I assume you want to mount it to /mnt/share.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /mnt/share   ext3   defaults   0   2
```
Save it and close down gedit window.  Then, create a new mount point and mount it.

```
sudo mkdir /mnt/share
sudo mount -a
```
Now, if you want to write to it without using sudo or gksudo, then you can change the ownership of /mnt/share from root to your login name.  _Assuming_ your login name is john, do

```
sudo chown -R john:john /mnt/share
ls -la /mnt
```

p.s.  The reason I use the mount point of /mnt/share instead of /media/share because there is a dude keeps following me around and whines about /media should be used by HAL for automount blah blah blah...

---

### Post by cdtech on 2008-11-16
You can just add this line to your /etc/fstab file:
```

sudo mkdir /media/sdb1
sudo gedit /etc/fstab
# Entry for /dev/sdb1:
/dev/sdb1 /media/sdb1 ext3 defaults 0 1
sudo mount -a (to mount without reboot)

```

**UPDATE::.**
Placing the mount point within the media directory will allow the device to be seen under "places"

---

### Post by empthollow on 2008-11-16
i believe this will work


```
/dev/sda2  /media/sda2 ext3    defaults   0 0
```

this assumes that the /media/sda2 exists and that the partition is formated to ext3.  adjust accordingly.

---

### Post by taurus on 2008-11-16
> **cdtech said:**
> You can just add this line to your /etc/fstab file:
```

sudo mkdir /media/sdb1
sudo gedit /etc/fstab
# Entry for /dev/sdb1:
/dev/sdb1 **[SIZE="5"][COLOR="Blue"]/media/sdb1[/COLOR][/SIZE]** ext3 defaults 0 1
sudo mount -a (to mount without reboot)

```

Whatever happens to use /mnt instead of /media?

---

### Post by cdtech on 2008-11-16
> **taurus said:**
> Whatever happens to use /mnt instead of /media?

See my updated post......

---

### Post by taurus on 2008-11-16
> **cdtech said:**
> See my updated post......

Then why were you all over my @$$ when I showed others to mount their drives to /media?  Talk about ironic.  :rolleyes:

If you mount something to /media, there will be an icon on the desktop so you can just double-click to access it.

---

### Post by cdtech on 2008-11-16
Why are you being so mean to me, I wasn't all over anyones @@! - Sorry about your feelings.

---

### Post by Comzee on 2008-11-16
Thanks Taurus!! That worked well. I also like that it doesn't show the icon on my Desktop that always annoyed me.

---

### Post by wieman01 on 2008-11-16
**taurus & cdtech, **

Relax & take a deep breath. This thread is about helping the OP, and nothing else! So I suggest that you stay on topic and leave your personal matters aside.

---

