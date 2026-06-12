---
title: "ubunto dosent show my hard drive"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Haim_el on 2007-06-10
Hey, I'm pretty new in linux and ubunto, and i have installed it since i need to support linux at my job :)

The issue i'm having is that one of my hard drives is not being showed in the computer.
I can see it in the hardware information, and when i type:  sudo lshw -C disk
i can see that partition.

This is an NTFS drive, that was working great in my previous installations of linux, and i don't know what i can do.

i tried running a search in the forums and the documentation, but couldn't find an answer.

What can i do to be see that drive in the computer screen?

Thank you so much for your help.

---

### Post by taurus on 2007-06-10
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Haim_el on 2007-06-10
> **taurus said:**
> [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Thank you for your response.
However, i was not able to mount the drive, even when i did a "force" mount, it told me that 
"fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
"
This is the same hard drive (different partition ofc) as linux file system

Thank again

---

### Post by djmaxmalta on 2007-06-10
> **Haim_el said:**
> Thank you for your response.
However, i was not able to mount the drive, even when i did a "force" mount, it told me that 
"fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
"
This is the same hard drive (different partition ofc) as linux file system

Thank again

how do you force mount??? and my ntfs partions are with ntfs-3g and it is not showing my partions and not even detection not mounting them how comes?? maybe that ubuntu did not update it to its stable release this is a major security risk to ubuntu and to windows!!!!

---

### Post by taurus on 2007-06-10
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```
Also, make sure you shutdown Windows properly (not hibernation stuff) first before you boot Ubuntu.

---

### Post by Haim_el on 2007-06-10
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             983       18260   138785156+   7  HPFS/NTFS
/dev/sdb2   *       18261       19400     9157050   83  Linux
/dev/sdb3           19401       19457      457852+   5  Extended
/dev/sdb5           19401       19457      457821   82  Linux swap / Solaris
```

This is what   ```
sudo fdisk -l
``` give me.

As i was saying the system recognize the drive and even assigned it with a drive name (it also appear in the /media directory.

I'm always doing a safe reboot in windows, and even tried to shut down the computer and the go directly to ubunto

10x for the help

BTW, the problem is with the SDB1 drive

---

### Post by djmaxmalta on 2007-06-10
> **Haim_el said:**
> ```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             983       18260   138785156+   7  HPFS/NTFS
/dev/sdb2   *       18261       19400     9157050   83  Linux
/dev/sdb3           19401       19457      457852+   5  Extended
/dev/sdb5           19401       19457      457821   82  Linux swap / Solaris
```

This is what   ```
sudo fdisk -l
``` give me.

As i was saying the system recognize the drive and even assigned it with a drive name (it also appear in the /media directory.

I'm always doing a safe reboot in windows, and even tried to shut down the computer and the go directly to ubunto

10x for the help

same here but this is what the terminal gave me it see them but dosent mount them??? how come?


[CENTER][LEFT][INDENT]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       10199    20482875    7  HPFS/NTFS
/dev/sda3           10200       14560    35029732+  83  Linux
/dev/sda4           14562       14593      257040   82  Linux swap / Solaris[/INDENT][/LEFT][/CENTER]

---

### Post by taurus on 2007-06-10
Which partition are you trying to mount here, /dev/sda1 or /dev/sdb1?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

---

### Post by djmaxmalta on 2007-06-10
> **taurus said:**
> Which partition are you trying to mount here, /dev/sda1 or /dev/sdb1?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

since mine are sda then i want to do both

and is there a manual for the linux codes??? for terminal i mean
djmaxmalta@djmaxmalta-laptop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
djmaxmalta@djmaxmalta-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

------------------edit----------------

your code done this and windows was a clean shutdown and its xp could it be that its 98% full?
> djmaxmalta@djmaxmalta-laptop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
djmaxmalta@djmaxmalta-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

---

### Post by taurus on 2007-06-10
> **djmaxmalta said:**
> same here but this is what the terminal gave me it see them but dosent mount them??? how come?


[CENTER][LEFT][INDENT]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       10199    20482875    7  HPFS/NTFS
/dev/sda3           10200       14560    35029732+  83  Linux
/dev/sda4           14562       14593      257040   82  Linux swap / Solaris[/INDENT][/LEFT][/CENTER]

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ntfs-3g
sudo mkdir /media/sda1 /media/sda2
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
```

---

### Post by Haim_el on 2007-06-10
did the mounting again (did it once or twice b4 with the manual you gave me)

didn't helped.

i don't know what i'm missing...

---

### Post by taurus on 2007-06-10
> **Haim_el said:**
> did the mounting again (did it once or twice b4 with the manual you gave me)

didn't helped.

i don't know what i'm missing...

When you said didn't help, was there an error message when you tried to mount it?

---

### Post by djmaxmalta on 2007-06-10
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ntfs-3g
sudo mkdir /media/sda1 /media/sda2
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
```



$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
djmaxmalta@djmaxmalta-laptop:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

keeps coming up and the ntfsfix where do i find it and what does it do???

---

### Post by Haim_el on 2007-06-10
> **taurus said:**
> When you said didn't help, was there an error message when you tried to mount it?

no, didnt got any error, it told me 

```
 sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

```

and i did restart the machine

---

### Post by taurus on 2007-06-10
djmaxmalta & Haim_el,

You two need to boot your machine into XP and run a scan disk of your ntfs partitions.  Then, shut it down properly and reboot it again.  Now, reboot into Ubuntu and see if you can mount those ntfs partitions this time.

---

### Post by djmaxmalta on 2007-06-10
> **Haim_el said:**
> no, didnt got any error, it told me 

```
 sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

```

and i did restart the machine

should i try that on mine??? or should defrag windows?

---

### Post by Haim_el on 2007-06-10
> **taurus said:**
> djmaxmalta & Haim_el,

You two need to boot your machine into XP and run a scan disk of your ntfs partitions.  Then, shut it down properly and reboot it again.  Now, reboot into Ubuntu and see if you can mount those ntfs partitions this time.

I'll give it a try.

Thanks.

---

### Post by djmaxmalta on 2007-06-10
> **taurus said:**
> djmaxmalta & Haim_el,

You two need to boot your machine into XP and run a scan disk of your ntfs partitions.  Then, shut it down properly and reboot it again.  Now, reboot into Ubuntu and see if you can mount those ntfs partitions this time.

okay i will do that and its gonna take a day damn windows

---

### Post by Haim_el on 2007-06-10
> **taurus said:**
> djmaxmalta & Haim_el,

You two need to boot your machine into XP and run a scan disk of your ntfs partitions.  Then, shut it down properly and reboot it again.  Now, reboot into Ubuntu and see if you can mount those ntfs partitions this time.

IT WORKED

OMG thank you so much:D

---

### Post by djmaxmalta on 2007-06-10
> **Haim_el said:**
> IT WORKED

OMG thank you so much:D

finally after 1 week of finding the solution thanks for your help this has been answered.

and if we all may agree that if u have the similar problem that me and the othere linux user try and see from our experience thanks.

---

### Post by pxxxner on 2007-06-14
> **taurus said:**
> djmaxmalta & Haim_el,

You two need to boot your machine into XP and run a scan disk of your ntfs partitions.  Then, shut it down properly and reboot it again.  Now, reboot into Ubuntu and see if you can mount those ntfs partitions this time.

i have the same problem, unfortunately i do not have windows.  is there another way?  the force mount command didn't work either.  thanks.

---

