---
title: "Drive is missing"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by Victim_of_Gluttony on 2007-10-03
I used to have my windows drive mounted in ubuntu, and just recently it stopped showing up and i dont know what i did to make it disappear.

---

### Post by slick666 on 2007-10-03
I would first check to make sure it isn't mounted at another location using 

```
df -h
```

in the terminal window.

This will show all mounted partitions in your system. If it's still not there I would try to mount it manually and see if there is an error.

---

### Post by taurus on 2007-10-03
Probably because you didn't shutdown Window properly.  Boot into Windows and scan it a couple of times.  Then, shut it down properly.  Now, boot into Ubuntu and see if you can mount it again.

Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by Victim_of_Gluttony on 2007-10-03
I have been having some problems with windows, but they have been going on long before my drive dissapeared. i keep doing chkdsk on window and it finds an error in volume bitmap, and chkdsk /f does nothing.... i hate computers sometimes

---

### Post by taurus on 2007-10-03
Is your Window partition ntfs?  What's the output of this command from a terminal?

```
sudo fdisk -l
```
Basically, you can still mount it with ntfs driver but you cannot mount it with ntfs-3g so you can only read from it but not write to it unless you fix whatever problem you have with Windows partition first.

---

### Post by Victim_of_Gluttony on 2007-10-03
> **taurus said:**
> Is your Window partition ntfs?  What's the output of this command from a terminal?

```
sudo fdisk -l
```
Basically, you can still mount it with ntfs driver but you cannot mount it with ntfs-3g so you can only read from it but not write to it unless you fix whatever problem you have with Windows partition first.
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18388   147701578+   7  HPFS/NTFS
/dev/sda2           18389       19361     7815622+  83  Linux
/dev/sda3           19362       19457      771120    5  Extended
/dev/sda5           19362       19457      771088+  82  Linux swap / Solaris

---

### Post by taurus on 2007-10-03
Try to mount it with

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
df -h
```

---

### Post by Victim_of_Gluttony on 2007-10-03
gluttony@gluttony-laptop:~$ sudo mkdir /media/sda1
Password:
mkdir: cannot create directory `/media/sda1': File exists

---

### Post by taurus on 2007-10-03
> **Victim_of_Gluttony said:**
> gluttony@gluttony-laptop:~$ sudo mkdir /media/sda1
Password:
mkdir: cannot create directory `/media/sda1': File exists

It just means that you already have /media/sda1.  Now, continue with the next two commands from above!

---

