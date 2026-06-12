---
title: "[SOLVED] kde 4.1 ntfs volume permissions"
date: 2008-11-05
forum: General Help
---

### Post by oliwally on 2008-11-05
I have two hard drives - one with Kubuntu 8.10 installed, and the other has windows. In Kubuntu I have pointed Firefox to the profiles folder in Windows, so that I have all my bookmarks and preferences the same in both systems. This has always worked well in 8.04 after a bit of tweaking of fstab. I was delighted to see that 8.10 recognized the windows hdd by default without trouble. However, my setup does not work and Firefox fails if I don't first 'visit' the ntfs hdd through dolphin. I'm asked for the root password and from then on all is well.

How and where do I fix this so all users can access & read/write the ntfs drive by default? I no longer understand the current fstab - where is the second (windows) ntfs hdd? Help please.

Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bad31ff5-7d1d-4bf5-8472-ab5fac5b577d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4ad1de1b-3fe5-4ead-a950-9246a199e239 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by cariboo on 2008-11-05
Go to System-->Administration-->Synaptic Package  Manager, and search for ntfs-config, install it and then use it to set up /etc/fstab

Jim

---

### Post by oliwally on 2008-11-06
Thanks so much Jim, but to no avail. I installed it, ran it, ticked the appropriate option (only one available), and have no change to my system.

KDE 3.5 had a neat menu through System Settings > Advanced, but in 4.1 it's no longer there.

Any other ideas please?

---

### Post by oliwally on 2008-11-07
Bump :)

> I have two hard drives - one with Kubuntu 8.10 installed, and the other has windows. In Kubuntu I have pointed Firefox to the profiles folder in Windows, so that I have all my bookmarks and preferences the same in both systems. This has always worked well in 8.04 after a bit of tweaking of fstab. I was delighted to see that 8.10 recognized the windows hdd by default without trouble. However, my setup does not work and Firefox fails if I don't first 'visit' the ntfs hdd through dolphin. I'm asked for the root password and from then on all is well.
 
 How and where do I fix this so all users can access & read/write the ntfs drive by default? I no longer understand the current fstab - where is the second (windows) ntfs hdd? Help please.

---

### Post by oliwally on 2008-11-11
Hi, I'm still hoping for some help with this issue please. Can anyone give me a hint or a link to look up..... please

I've installed MountManager through Synaptic and it gives all the options. But somehow the settings won't stick, and when I force them to by saving a separate fstab (one of the options of MountManager) and overwriting the old one, the hdd won't mount at all

It appears that by default my hdd is not even listed in fstab and somehow gets mounted some other way, through some other process.

---

### Post by oliwally on 2008-11-13
:( Help please......

> I've installed MountManager through Synaptic and it gives all the options. But somehow the settings won't stick, and when I force them to by saving a separate fstab (one of the options of MountManager) and overwriting the old one, the hdd won't mount at all

It appears that by default my hdd is not even listed in fstab and somehow gets mounted some other way, through some other process.

---

### Post by oliwally on 2008-11-24
Hello again. 
I'm still stuck on this issue. Is there anyone out there who can help me please?

> I have two hard drives - one with Kubuntu 8.10 installed, and the other has windows. In Kubuntu I have pointed Firefox to the profiles folder in Windows, so that I have all my bookmarks and preferences the same in both systems. This has always worked well in 8.04 after a bit of tweaking of fstab. I was delighted to see that 8.10 recognized the windows hdd by default without trouble. However, my setup does not work and Firefox fails if I don't first 'visit' the ntfs hdd through dolphin. I'm asked for the root password and from then on all is well.

---

### Post by oliwally on 2008-12-06
Solved, but man, oh man, oh man, oh man. The simplest of mistakes......

I wrote the appropriate line into fstab
```
/dev/sdb1       /media/winxp    auto nouser,atime,auto,rw,nodev,exec,nosuid 0 0
```  after creating a winxp directory in /media, and that had always worked anyway - the hdd auto-mounted and I had rw access.

I found more help on how to do the mounting here: [http://ubuntuforums.org/showthread.php?p=6196675#post6196675](http://ubuntuforums.org/showthread.php?p=6196675#post6196675)

But....:oops:  I forgot to tell my Firefox and Thunderbird profiles to point to the newly created /media/winxp mount point..... it was sill pointing to /media/disk (and thus needed the root pw).](*,)

---

