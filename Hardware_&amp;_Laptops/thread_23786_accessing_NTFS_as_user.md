---
title: "accessing NTFS as user"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by aje on 2005-04-04
I have an NTFS drive on /dev/sda1.  I have successfully mounted it as root and I have accessed files on it.  I am trying to be able to access it as a regular user but I seem to be doing something wrong.  I still get permission denied when I try to access it as a user, but can access it perfectly fine as root.  

Here's my fstab line for the drive:
```
/dev/sda1       /media/usbhd          ntfs    ro,users,umask=000   0     0
```

What am I doing incorrectly?

---

### Post by iomicifikko on 2005-04-06
[QUOTE=aje]I have an NTFS drive on /dev/sda1.  I have successfully mounted it as root and I have accessed files on it.  I am trying to be able to access it as a regular user but I seem to be doing something wrong.  I still get permission denied when I try to access it as a user, but can access it perfectly fine as root.  

Here's my fstab line for the drive:
```
/dev/sda1       /media/usbhd          ntfs    ro,users,umask=000   0     0
```

What am I doing incorrectly?[/QUOTE]
 --> im a newbie <--

when u are root just right click on the directory, select properties and change permissions (for example put readable by anyone)

anyway i think those fstab settings are wrong couse for ntfs volumes u should put "ntfs    umask=0222      0       0"  

remember u can readonly ntfs volumes, not fully implemented in linux

byez

ps: give always a look at [http://ubuntuguide.org](http://ubuntuguide.org) for these kind of problems

---

