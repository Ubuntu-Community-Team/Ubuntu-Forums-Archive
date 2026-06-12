---
title: "Automount internal media"
date: 2008-11-19
forum: Hardware
---

### Post by rhcm123 on 2008-11-19
I have a partition on my main hdd that holds all my data. It's a windows partition, so it's formatted NTFS. I would like to automount that at boot (because my ubuntu partition is very small, 5 gb, all data is stored there) so i dont have to do it through the GNOME panel. It's not particularly hard, just annoying.

THANKS!

---

### Post by taurus on 2008-11-19
Just install ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by rhcm123 on 2008-11-19
> **taurus said:**
> Just install ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

ut-oh! "enable write to internal device" is grayed out!"
why could this be?

---

### Post by taurus on 2008-11-19
What happens if you try to mount it by hand from a terminal?  Any error message?

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g **/dev/sda1** /media/windows
```
Replace **/dev/sda1** with the right partition.

---

### Post by rhcm123 on 2008-11-19
> **taurus said:**
> What happens if you try to mount it by hand from a terminal?  Any error message?

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g **/dev/sda1** /media/windows
```
Replace **/dev/sda1** with the right partition.

it mounts it right away, no problems.
I noticed that, if I would mount it with the GNOME applet, a LAPTOP folder would appear in /media (LAPTOP is the name of the drive in windoz) and if i unmounted it it would vanish.)

---

### Post by taurus on 2008-11-19
Well, you can add an entry in /etc/fstab by hand for your ntfs partition if you wish.

```
gksudo gedit /etc/fstab
```
And add this line to the end of it.

```
/dev/sda1   /media/windows   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it and exit gedit editing window.  Remember, you need to replace /dev/sda1 with the right one or you can use the UUID for that partition.  Also, make sure you create that new mount point, /media/windows, or whatever one you want to use.

```
sudo blkid  <-- for UUID
sudo mkdir /media/windows  <-- for mount point
```

---

### Post by rhcm123 on 2008-11-19
Thank you, it worked!
Now I actually have a background when i login!
(And with both sda1 and my server automounting, i have to do nothing at login :)!)

---

