---
title: "Ubuntu 7.04 doesn't see my external HDD"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by Tezcatlipoca on 2007-09-02
I've just got round to finally installing 7.04, in place of 6.10.


It's a fresh install, not an upgrade.


It's fully up to date.


Everything seems to be working OK, except...


My Seagate USB2 external HDD, which I can't see or access.

It worked perfectly under 6.10.


It's set to mount removable drives/media when hot plugged / inserted.

But when I turn on the HDD... nothing.

---

### Post by taurus on 2007-09-02
Maybe you need to mount it by hand first before you can access it.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

p.s.  Make sure you USB drive is plugged with power on first.

---

### Post by vanadium on 2007-09-02
I never had problems with USB drives under Feisty. It should be mounted automatically under /media with an icon on the desktop. Sure all connections are OK?

To check whether the drive is seen by the system, type "sudo fdisk -l". If the volume is mounted, it should also appear in the output of "mount". If you post the output of these commands here, people might be able to help you in a more specific way to see where the problem is.

---

### Post by Tezcatlipoca on 2007-09-02
If I enter "sudo fdisk -l", it does actually list the drive 

> 
Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       38913   312568641    c  W95 FAT32 (LBA)


But it isn't listed when I enter "mount".


It always used to automatically mount it under 6.10... if I turned it on, I'd get an icon on the desktop, & it would appear in media.

The connections are fine... I've checked them, & also tried different USB sockets. Plus, if I boot into XP, the drive appears as normal.


Stupid question time... if it won't mount automatically, what's the best way to mount it manually, given that I don't have the drive turned on all the time?

:)

---

### Post by taurus on 2007-09-02
```
sudo mkdir /media/sdf1
sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by Tezcatlipoca on 2007-09-02
Cheers :D

---

### Post by Tezcatlipoca on 2007-09-02
OK, sorry, one last newbish question...


As it won't mount automatically for some reason, how can I turn 

> 
sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000

into an executable script I can just click on to mount it when needed?

... and the reverse, to unmount it before turning it off?


Thanks :)

---

### Post by taurus on 2007-09-02
Is that drive always connected to your machine?  You can edit /etc/fstab and add an entry for it.

```
gksudo gedit /etc/fstab
```

And add this line to the end of it.
```
/dev/sdf1   /media/sdf1   vfat   iocharset=utf8,umask=000   0   0
```
And if you want to mount it, run

```
sudo mount -a
```
And if you want to unmount it, run

```
sudo umount /media/sdf1
```
p.s.  Make sure you unmount it first before you turn off the power.

---

### Post by Tezcatlipoca on 2007-09-02
Yeah, it's always connected, just not always turned on.


Thanks for the help, I'll edit fstab :)

---

### Post by vanadium on 2007-09-02
You will need to add the option "noauto" to the fstab entry. Otherwise, the system wil attempt to mount during bootup even if the drive is not powered on. Additionally, you should mount it with

sudo mount /media/sdf1

The command mount -a does attempt do remount all that is in fstab. You only want to mount sdf1, though.

The question remains why Ubuntu Feisty fails to mount your drive automatically, though ...

---

### Post by Tezcatlipoca on 2007-09-02
Cheers.

Should I just add ",noauto" straight after "iocharset=utf8,umask=000" ?

---

### Post by vanadium on 2007-09-02
Yes indeed. It is one of the options. Success!

---

### Post by Tezcatlipoca on 2007-09-02
Great. Just changed :)

---

