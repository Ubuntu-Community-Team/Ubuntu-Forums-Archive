---
title: "Western Digital External HDD issues!"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by BruceWayne on 2006-03-12
Well I searched and searched for my answer but I cant find someone with a similar problem. I plugged in my USB and it just doesnt do anything. Almost like the PC didnt even know I plugged anything in. I brought up console and typed in mount and I get this:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

Please help anyone..

---

### Post by taurus on 2006-03-12
I just went through a similar post not that long ago.  Again, mount actually doesn't mount anything!  It just shows you what has been mounted so if you want to mount your external HD which I assume it has a FAT32 filesystem, then do these from a terminal,
```

sudo mkdir /media/external
sudo mount -t vfat /dev/sda /media/external
mount

```

---

### Post by BruceWayne on 2006-03-12
Well after the second command I get this:

mount: special device /dev/sda does not exist

---

### Post by taurus on 2006-03-12
Okay, plug in your USB HD and paste the output of the following command here then,
```

dmesg | tail 

```

---

