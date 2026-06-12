---
title: "[help]problems in auto-mount windows partition and fstab"
date: 2012-05-30
forum: Hardware
---

### Post by xumaomao on 2012-05-30
Hi
I am new to ubuntu and now having some problems in editing the fstab file.

At first everything works all fine, the windows partitions are auto-mounted at boot, and I have access and permissions to them. But somehow:confused: I installed ntfs-config, and then uninstalled it because error message pops up every time I boot. I am not sure whether this has modified my fstab or not. Later I backed up the fstab, added noauto,user options to the windows partitions, and they were no longer accessible. So I recovered fstab using the back-up. But I lost some permissions to those windows files/directories.

Not sure I am describing it clearly. Basically I did something that makes me lost permissions to windows files, but I am not sure what it is because I recovered fstab by back-up, so it could be ntfs-config, but I have no idea of what the fstab looked like before ntfs-config installation.

This is a copy of my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda11 :
UUID=4fbb670d-3a0b-44df-83d1-59095081354f    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda9 :
UUID=926e2475-9582-487c-ba48-736655ee1547    /boot    ext4    defaults    0    2
#Entry for /dev/sda10 :
UUID=099795b2-ebea-4e98-9b35-b40cd0eceb81    /home    ext4    defaults    0    2
#Entry for /dev/sda1 :
UUID=64BC278DBC2758B6    /media/M_fM__VM_0M_eM__JM__M_eM__MM_7    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda2 :
UUID=8A2EF9D02EF9B573    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda3 :
UUID=687071027070D870    /media/sda3    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda5 :
UUID=8024234724233F90    /media/sda5    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda7 :
UUID=900867A708678B54    /media/sda7    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=78044C1D044BDCAE    /media/&#26032;&#21152;&#21367;    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda8 :
UUID=a5140d75-9d64-4dd7-8971-2477c911c4bf    none    swap    sw    0    0Please just ignore those Chinese characters and some very strange disk name...the umask codes and different options really confused me. What does the first digit in 'umask=0222' stands for? Am I not the root and should have full permission?

What do I need to do to set, for instance, the sda5 partition to auto-mount, with all permissions, and some others non-auto-mount but still have permission to?

Many many many many thanks~~~~

---

### Post by oldfred on 2012-05-30
I am no expert on this, your entry does not look far from these suggestions. If you have trouble with some of the entries add # to convert to a comment until you decide if you want to edit and mount or not.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
```
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

```Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Has info on using 0022, but normally the the first number is for groups, not sure about fstab entries.
[http://opensuse.swerdna.org/susentfs.html](http://opensuse.swerdna.org/susentfs.html)

Options:
[http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g)
Better than man mount info on NTFS i.e. has windows_names explanation:
[http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

Hide mount with defaults
```
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
```
Hide windows mount with noauto: 777 is no permissions at all
```
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
```

---

### Post by xumaomao on 2012-06-02
Thanks for your very detailed reply.

Now I could be sure to say that the ntfs-config stuff does modify user's fstab file. (should be obvious, shouldn't it?)

After a long process of testing and try and error I finally came up with a setup that works. Sometimes I have to mount a partition manually to 'activate' it, otherwise it wouldn't be mounted automatically at boot. Very tricky.

Anyway, thanks again.:)

And I would like suggest that anyone who wants to try ntfs-config, pysdm or anything else, backup the fstab file first.

---

### Post by coffeecat on 2012-06-02
> **xumaomao said:**
> 
And I would like suggest that anyone who wants to try ntfs-config, pysdm or anything else, backup the fstab file first.

@xumaomao, I would go further than that and suggest to anyone who is considering trying ntfs-config or pysdm that they do not! Both of those apps were developed in about 2005, if I remember correctly, and have been unmaintained since. They can both cause significant problems.

---

