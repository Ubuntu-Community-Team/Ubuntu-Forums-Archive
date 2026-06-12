---
title: "[SOLVED] Maxtor One Touch won't mount"
date: 2008-11-02
forum: General Help
---

### Post by PoopyTheJ on 2008-11-02
I have a Maxtor One Touch which I can't get to mount on Ubuntu, when plugging it in the system doesn't recognize anything has been plugged in. Other externals work fine plugged to the same USB connection. The output of dmesg | tail gives me...

[16351.882800] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[16351.882803] hub 5-0:1.0: hub_port_status failed (err = -32)
[16381.848363] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[16381.848369] hub 5-0:1.0: hub_port_status failed (err = -32)
[16381.850002] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[16381.850005] hub 5-0:1.0: hub_port_status failed (err = -32)
[16411.823177] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[16411.823184] hub 5-0:1.0: hub_port_status failed (err = -32)
[16411.824704] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[16411.824707] hub 5-0:1.0: hub_port_status failed (err = -32)

I assume that means a problem with the drive itself? Anything I can do to resolve this to at least pull the data off?

---

### Post by PoopyTheJ on 2008-11-06
Ok, now I can see the drive in Ubuntu, however when I try to mount the drive I get this error

[IMG]http://img266.imageshack.us/img266/8535/onetoucherrorry4.png[/IMG]

I can't use the command described because there is a space in the device name. I don't have windows so I can't use the first option. What's the solution here?

---

### Post by sisco311 on 2008-11-06
try:
```
sudo mount -t ntfs /dev/sdc1 /media/OneTouch4\ Plus -o force
```
or
```
sudo mount -t ntfs /dev/sdc1 "/media/OneTouch4 Plus" -o force
```
or create a different mount point:
```
sudo mkdir /media/test
sudo mount -t ntfs /dev/sdc1 /media/test -o force
```

---

### Post by PoopyTheJ on 2008-11-06
Sweet! That worked, now I just formatted another drive to copy all of this info to as I'm unsure of the reliability of the drive due to the problems mounting and I couldn't get a windows box at work to use it so I'm backing the files up. Anyways since I formatted the drive when I try to write to the drive I get an error which says I don't have permission to write to the drive, why is that and what can I do to fix it?

---

### Post by sisco311 on 2008-11-07
if you formatted the drive to ext2/ext3, then you need to set the owner of the drive:
```
sudo chown -R *your-user-name:your-group* /media/*mount-point*
```
where *your-user-name* is your login name,

*your-group* is your primary group, usually is the same as your log in name,

/media/*mount-point* is the mount point of the partition(ex. /media/OneTouch4\ Plus)

example:```
sudo chown -R PoopyTheJ:PoopyTheJ /media/OneTouch4\ Plus
```

read more about linux file permissions here:[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by PoopyTheJ on 2008-11-07
Thank you! Also thanks for the resource, I was looking for something along those lines but dumbed down enough for me to understand!

---

