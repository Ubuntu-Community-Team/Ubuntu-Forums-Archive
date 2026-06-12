---
title: "why doesn't my usb external hard drive mount?"
date: 2009-02-08
forum: Hardware
---

### Post by eggy1962 on 2009-02-08
Hi, decided to start another thread as i was not getting much help when i joined another..
I am trying to use my external hard drive(usb) but it is ntfs formatted and is not allowing the mount... the pc sees the drive in "places" but i just cannot access it and i want to copy some 30 gig of mp3's over to my ubuntu 8.10 desktop hard drive.
i have installed  ntfs-3g
 Please note i am a linux novice and  any help would have to be  easy ish for me to follow.
mark

---

### Post by taurus on 2009-02-08
Did you use the _safely remove hardware_ option in windows when you last used the drive?  You're not supposed to just unplug it from the computer after you are finished using it.  You should unmount it first before you unplug it.

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by eggy1962 on 2009-02-08
this is what i have with the drive unplugged
mark@mark-desktop:~$ sudo fdisk -1
[sudo] password for mark: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
mark@mark-desktop:~$

---

### Post by eggy1962 on 2009-02-08
oops mistype  try again

mark@mark-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012c55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14217   114198021   83  Linux
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda5           14218       14593     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16361635

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS
mark@mark-desktop:~$ 


this is with the drive plugged in

---

### Post by taurus on 2009-02-08
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
And when you are done using your external drive, try to unmount it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by eggy1962 on 2009-02-08
mark@mark-desktop:~$ sudo umount /media/sdb1
[sudo] password for mark: 
umount: /media/sdb1: not found
mark@mark-desktop:~$ sudo unmount /media/sdb1
sudo: unmount: command not found
mark@mark-desktop:~$ 

i do know about the unmounting in linux but its very difficult to unmount something that won't mount in the first place..
now my usb memory stick works fine i assume because thats fat 32

---

### Post by taurus on 2009-02-08
Have you already mounted /dev/sdb1 to /media/sdb1?  You cannot unmount something that is not currently mounted.

```
df -h
```

---

### Post by eggy1962 on 2009-02-08
lost me  don't know how... to be honest should we be struggling to mount external hardware?? its 2009 surely it should automount the usb stick does

---

### Post by taurus on 2009-02-08
> **eggy1962 said:**
> lost me  don't know how... to be honest should we be struggling to mount external hardware?? its 2009 surely it should automount the usb stick does

Again, Ubuntu would automount it only if you use the safely remove hardware option (little icon at the bottom right, next to clock) in windows first.  If you just yank it out when you are done using it, then you need to use ntfsfix to fix it or force mount it in Ubuntu.  I have already gave you all the steps to do fix it but I guess it's up to you if you want to follow them or not.

---

### Post by eggy1962 on 2009-02-08
i have not been able to use it, i am not dual booting so there is no windows, your steps have lost me a bit if i post a report/copy of what i see in the terminal window  then i have done that step if i haven't then im lost

---

### Post by taurus on 2009-02-08
If you don't understand a command or get an error message when you run it, then post the command with the error message.  However, I have no idea how to help when you just say "I'm lost".

Just run one command at a time from a terminal.  If it asks for a password, use the same one that you log in with.  It won't display on the screen when you type it so just make sure you type the right one and hit Return.

---

### Post by eggy1962 on 2009-02-08
i got lost on your post number 5 going back to try them again i missed the first section of that post

---

### Post by eggy1962 on 2009-02-08
you will be pleased to note that when i went back and did the bit i missed out it went well hard drive now mounts and i can access the files.... i won't forget to unmount it before removing
Thank you for your patience

---

