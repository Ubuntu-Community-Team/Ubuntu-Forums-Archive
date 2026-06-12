---
title: "after update, external HDD read only and one not detected"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by xfceuser on 2009-07-04
hi 
I am using hardy 8.04.
I have an external ntfs hard disk via usb.
it was working before, as I had installed ntfs-3g and also ntfs config.

but 7 days ago after updating it has become read only, I cant change the content anymore. I tried ntfs config but it doesnt help. 

I will appreciate a lot if you could help.

---

### Post by merlinus on 2009-07-04
Is it being mounted by /etc/fstab?  If so, you might post the contents of that file.

Alternatively, if mounted, navigate to it via nautilus and look at the permissions.

---

### Post by xfceuser on 2009-07-05
thanks for your reply.
the external HDD is at /dev/sdb but there is no entry for it at the /etc/fstab and changing the ntfs config also doesnt add anything to /etc/fstab, I am wondering how it gets mounted now without fstab?
can it be the problem?
also I am using thunar, which should not be the problem ( I tried it also on nautilus and ubuntu but the same problem), it says that the folder in the /media/ that the HDD is mounted is belonging to the root user, but I also run thunar as root and still couldn't edit anything on the HDD.

---

### Post by merlinus on 2009-07-05
What is the result of

```
sudo fdisk -l
```

and is the hdd plugged in all the time?

---

### Post by xfceuser on 2009-07-05
no I plug usb of HDD only sometimes,

the output is like this;
Disk /dev/sda 
/dev/sda1     Linux
/dev/sda2     Extended
/dev/sda5     Linux swap / Solaris

Disk /dev/sdb
/dev/sdb1      HPFS/NTFS

so that the usb HDD is at /dev/sdb

when I want to make a folder or edit some thing it says "Failed ... operation not supported"

---

### Post by hal_bg on 2009-07-05
I have the same problem but with my only HDD on my laptop
after the upgrade from 8.10 to 9.04 /dev/sda2 stopped showing in nautillus computer view. Only /dev/sda3 is shown.  

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1917    15358140    7  HPFS/NTFS
/dev/sda3   *        1918        6487    36705867+   7  HPFS/NTFS
/dev/sda4            6488       19457   104181525    5  Extended
/dev/sda5            6488        7216     5855661   82  Linux swap / Solaris
/dev/sda6            7217       19457    98325801   83  Linux


However sda2 can be mounted with mount command. It is annoying because hda2 is used as a common storage for win and linux, and the only thing I use windows is to sync my iphone. So sda2 is the place where I put music, videos apps then go to windoes just to sync the iphone.

Can anybody help?

hal

---

### Post by xfceuser on 2009-07-09
maybe this can help, does anyone know the exact step by step process that linux (ubuntu) does when one plugs in a usb drive till it gets mounted?

---

### Post by hal_bg on 2009-07-09
looks like nobody can help...
maybe we should post a bug?!?

---

### Post by xfceuser on 2009-07-09
i think maybe the problem can be solved by adding something to /etc/fstab but don't know exactly what, and moreover why before it was working fine only by nfs-config utility?

---

### Post by xfceuser on 2009-07-15
on the external hdd, mounted as read-write, sometimes its possible to create a directory, sometimes not ...
it says "cant create the directory,operation not supported"
but sometimes it does!
another hdd mounted only as read-only!

---

### Post by ezsit on 2009-07-15
> on the external hdd, mounted as read-write, sometimes its possible to create a directory, sometimes not ...
it says "cant create the directory,operation not supported"
but sometimes it does!
another hdd mounted only as read-only!

Backup your data and expect the drive to completely fail at some point in the not-too-distant-future. Flaky drive behavior is usually a symptom of hardware failure.

---

### Post by xfceuser on 2009-07-15
maybe, but it was working fine before the update,and what about the other usb hdd that is mounted only read-only?

---

### Post by ftgibson on 2009-07-17
Hi All,
  I have been having issues since upgrading my Ubuntu also. It would not recognize my usb thumb drive, my external Western Digital HD and I was about to give up.  Alas I found the MountManager 0.2.6 in the Synaptic Package Manager.   All probs seem to have been taken care of as of now.  Let me know if this helps you mount your devices.

Sincerley,
Amie

---

### Post by xfceuser on 2009-07-18
so it seems that the mounting problem of usb hdd's after update happened to many peoples!
anyway, I couldnt install MountManager because of dependency problems.

---

### Post by xfceuser on 2009-07-18
from here;
[http://www.ntfs-3g.org/support.html#filecreate](http://www.ntfs-3g.org/support.html#filecreate)

it seems to be a bug of ntfs-3g, but how to update ntfs-3g to the latest version, I dont think that the ubuntu version is the latest one?

---

### Post by xfceuser on 2009-07-18
so I installed latest ntfs-config and also ntfs-3g directly from their website (which are newer than the one that comes with ubuntu).

it only cannot be mounted automatically in thunar (it says that "you do not have enough privilege to mount ..." 

but now I can manually mount and unmount the hdds in the terminal and everything works fine.

---

