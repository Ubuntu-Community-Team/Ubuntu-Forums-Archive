---
title: "How do I change ownership of a hard drive?"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by Antarctica on 2008-03-06
Hey all, I'm having a problem with my 80 GB slave hard drive.  Everytime I want to access it, I have to type my password and become root.  Is there any way I can change the permissions to add me as a user with full ownership instead of solely root?  The hard drive is currently mounted at /media/disk and located at /dev/hda (or hda1 for the primary partition), and it is formatted as ext3.  Thank you in advance.

I think I found the solution:  chown [username] [location]

I used chown on /dev/hda, /dev/hda1, and /media/disk.  I got full access to the disk.  Which location do you think did the trick?

---

### Post by taurus on 2008-03-06
/media/disk.  Mount point is the one you want to change ownership, not the drive itself.

---

### Post by Antarctica on 2008-03-06
Awesome dude.  Now try this... When I go to Computer, I try to access the hard drive from there (which says 74.5 GB Volume) and that's where it asks me for my password.  Any way to keep it from asking for my password?

---

### Post by taurus on 2008-03-06
You mean it asks for your password when you try to access /media/disk?

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
id
```

---

### Post by hotballz87 on 2008-03-07
so i have a problem with doing this too, 

i bought  a new hard drive and installed ubuntu on it, and have an older 160 gig with windows on it, and want to format it to put my music and movies on, but its under the root user and i cant get in to format or do anytihng to it.

i tried the "chown /media/PRESARIO

(PRESARIO is the name of the drive...)  

here is what i get out of it, 

```

steve@steve-desktop:~$ chown steve /media/PRESARIO
chown: changing ownership of `/media/PRESARIO': Read-only file system

```

but it does nothing to the drive, it still says the owner is root....

---

### Post by taurus on 2008-03-07
> **hotballz87 said:**
> so i have a problem with doing this too, 

i bought  a new hard drive and installed ubuntu on it, and have an older 160 gig with windows on it, and want to format it to put my music and movies on, but its under the root user and i cant get in to format or do anytihng to it.

i tried the "chown /media/PRESARIO

(PRESARIO is the name of the drive...)  

here is what i get out of it, 

```

steve@steve-desktop:~$ chown steve /media/PRESARIO
chown: changing ownership of `/media/PRESARIO': Read-only file system

```

but it does nothing to the drive, it still says the owner is root....

What is the filesystem of /media/PRESARIO?

```
sudo fdisk -l
df -h
```

---

### Post by hotballz87 on 2008-03-07
sudo fdisk -l 

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18662   149902483+  83  Linux
/dev/hda2           18663       19457     6385837+   5  Extended
/dev/hda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18550   149002843+   7  HPFS/NTFS
/dev/hdb2           18551       19457     7285446    c  W95 FAT32 (LBA)

Disk /dev/sda: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1968      503792    b  W95 FAT32

```

and
df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             141G   20G  114G  15% /
varrun                1.3G  108K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
procbususb            1.3G  132K  1.3G   1% /proc/bus/usb
udev                  1.3G  132K  1.3G   1% /dev
devshm                1.3G     0  1.3G   0% /dev/shm
lrm                   1.3G   13M  1.3G   2% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             492M  8.0K  491M   1% /media/STEVE
/dev/hdb1             143G  8.4G  134G   6% /media/PRESARIO

```

---

### Post by taurus on 2008-03-07
Try

```
sudo umount /media/PRESARIO
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mount -t ntfs-3g /dev/hdb1 /media/PRESARIO
ls -la /media
```

---

### Post by hotballz87 on 2008-03-07
i got to 

sudo mount -t ntfs-3g /dev/hdb1 /media/PRESARIO

and got this message:


```
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```

i cant boot windows with this drive because windows is corrupt on it and wont fully start

---

### Post by taurus on 2008-03-07
```
sudo mount -t ntfs-3g /dev/hdb1 /media/PRESARIO -o force
ls -la /media/PRESARIO
```

I assume you want to backup your important files on /dev/hdb1 since you can't boot from it anymore!

---

### Post by Antarctica on 2008-03-07
Sorry, I've been away at school, and then I decided to reinstall Ubuntu.  Basically when I login and want to access the second hard drive through Computer, 74.5 GB Volume:  disk, I get a password dialog saying that access to internal disk is restricted to administrators, and then I enter my password.  The mount point again is /media/disk.  I don't mind typing in the password, but it would be convenient if I could bypass that, so any suggestions?

---

### Post by sloggerkhan on 2008-03-07
on my computer, all internal disks mounted in /media defaulted to root ownership.
So I did:

alt-f2
gksudo nautilus /media
right click > properties on each of the drives I wanted
permissions tab
set owner to myself
set group to users
both with create/delete folder access
closed

refreshed nautilus as my user, and immediately had access.

NEVER do this to anything but media disks that you want accessible and shared by users.

---

### Post by taurus on 2008-03-07
> **sloggerkhan said:**
> on my computer, all internal disks mounted in /media defaulted to root ownership.
So I did:

alt-f2
gksudo nautilus /media
right click > properties on each of the drives I wanted
permissions tab
set owner to myself
set group to users
both with create/delete folder access
closed

refreshed nautilus as my user, and immediately had access.

NEVER do this to anything but media disks that you want accessible and shared by users.

But doesn't it depend on the filesystem?

---

### Post by sloggerkhan on 2008-03-07
> **taurus said:**
> But doesn't it depend on the filesystem?

I have no idea what you are trying to ask.

---

### Post by taurus on 2008-03-07
> **sloggerkhan said:**
> I have no idea what you are trying to ask.

You said you could just run nautilus as root and change ownership/group with the right button in the Properties.  My question is doesn't it depend on the filesystem?  Can you change ownership/group like that with ntfs filesystem?

---

### Post by sloggerkhan on 2008-03-07
Oh. I'm not sure.
I can vouch that it works for xfs, jfs, reiserfs, and ext3, but I don't have any ntfs partitions, drives, disks, or devices.

---

### Post by taurus on 2008-03-07
> **sloggerkhan said:**
> Oh. I'm not sure.
I can vouch that it works for xfs, jfs, reiserfs, and ext3, but I don't have any ntfs partitions, drives, disks, or devices.

And that is my point.  You cannot change ownership/group with nautilus or chown if the partition is ntfs or vfat.

That's why I asked him about what filesystem is his /media/disk.

```
sudo fdisk -l
df -h
```

---

### Post by sloggerkhan on 2008-03-07
Are you sure about that? I know you can do it with vfat.

---

### Post by taurus on 2008-03-07
> **sloggerkhan said:**
> Are you sure about that? I know you can do it with vfat.

I have no idea what you are trying to ask.

---

### Post by michiel33 on 2008-04-27
Well, I have this problem with an NTFS formatted drive, how do I change the ownership now? I use the drive commonly between Windows and Ubuntu on my dual-boot system.

It used to work when the (USB) drive was automatically mounted! Somehow I lost the USB automount of that drive! :-( dont understand why! Now I mount it with a script but that does not make me owner, very annoying.

Any idea how to restore the automount function for that drive?


Thanks!! Michiel.


> **taurus said:**
> And that is my point.  You cannot change ownership/group with nautilus or chown if the partition is ntfs or vfat.

That's why I asked him about what filesystem is his /media/disk.

```
sudo fdisk -l
df -h
```

---

