---
title: "Accessing a fat32 partition"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by Blazeix on 2006-04-01
Hi, I am dual booting Windows XP and Ubuntu, and I have a separate fat 32 partition I would like to access from both of them. I have it working for windows, but not for linux. It is not under /mnt or /media. This is the output i get for the mount command:

mount -l
/dev/sda3 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

Can anyone help me? Thanks.

---

### Post by taurus on 2006-04-01
Did you include an entry in /etc/fstab it would be mounted automatically upon boot?  If not, you need to edit your /etc/fstab from a terminal and add something like
```

sudo mkdir /media/share
sudo gedit /etc/fstab
(Then, add this line to the end of it...)
/dev/hda4  /media/share  vfat  defaults,umask=0000  0  0
(assuming that the fat32 is on /dev/hda4...)

```
Now, save it and run this at the prompt...
```

mount -a

```
You should see your fat32's partition in /media/share now!

---

### Post by Blazeix on 2006-04-01
Thanks, how do I tell where the fat32 partition is? is there a way where I can see the size of partitions on my hard drive and their corresponding locations?

---

### Post by taurus on 2006-04-01
Since you mount it on /media/share, then your fat32 should be in /media/share!!!  And if you want to see the size and location of all your partitions, then run this from a terminal...
```

df -h

```

---

### Post by Blazeix on 2006-04-01
I meant how to I tell if the partition is called sda1 or sda4 or hdaX. I followed your instructions, guessing on the name (which happened to be sd6), and it works great! thanks.

---

### Post by Blazeix on 2006-04-01
Well, I thought it was working, but I can't seem to read or write to it. Right clicking and changing the permissions doesn't seem to work. A friend of mine said that I need a different kernel, but he wasn't sure. I'm using the most updated version of Ubuntu.

---

### Post by Blue1k on 2006-04-02
Try the following command: (works for me)

/dev/hda1    /media/storage   vfat noauto,users,rw,exec,umask=000  0	  0


Where hda1 is the partion for my fat32 drive.

---

