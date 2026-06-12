---
title: "fstab not resolving remote location"
date: 2016-12-06
forum: Hardware
---

### Post by andrea-c on 2016-12-06
Hello.
I've a synology nas RS3614xs in the office and I made a small partition for backing up our main server.
I can easily mount and r/w to the share with the mount command but when I try to add the partition to the fstab

```
//10.11.7.6/volume1/OKAYlinux-backups/ /mnt/sdd1 cifs username=1,password=2,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp 0 0
```


sudo mount -a return this 

```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


And, from var/log/syslog
```
CIFS VFS: cifs_mount failed w/return code = -6
```

Is anyone aware of special settings/condition for mounting/resolving a NAS volume address?

Thank you

---

### Post by TheFu on 2016-12-06
Does /mnt/sdd1 exist? Can 10.11.7.6 be ping'd?
[https://lists.samba.org/archive/linux-cifs-client/2007-August/002169.html](https://lists.samba.org/archive/linux-cifs-client/2007-August/002169.html) - says it isn't a valid share, so test it from a Windows machine.

BTW, would be smart to put the required credentials into a separate file that only root can read.  That option is ... credentials=/full/path/to/file

For files like this, I usually shove them into /root/bin/ ... that location will be locked down (700) and should be included in backups.

---

### Post by andrea-c on 2016-12-07
I created the mnt/sdd1 and when I use "mount" command everything works fine
When mounting it on Windows everything is fine....

Yeah I have a credential file in place. But I'm lazy and do things step  by step checking that everything works fine and then moving to  security-related tasks

---

### Post by TheFu on 2016-12-07
mnt/sdd1 is different from /mnt/sdd1 unless you run this from /.  Please check that and be careful about leading / characters. They are important.

There were lots of useful commands in the link. When you enable verbose mode, some useful output should come out.

---

### Post by andrea-c on 2016-12-13
Ok so **mount -av** returns



```

mount: UUID=d85c136c-c30b-4ef7-9c17-8ffb6fe2951a already mounted on /boot
mount: //10.11.7.10/Promise Pegasus/ already mounted on /media/share
mount: you didn't specify a filesystem type for /dev/disk/by-uuid/8ae5dcc0-1973-4a12-a177-f756465974b6
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying ext3
mount.cifs kernel mount options: ip=10.11.7.6,unc=\\10.11.7.6\volume1,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp,uid=1000,gid=1000,user=LADIDA,prefixpath=OKAYlinux-backups/,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=10.11.7.6,unc=\\10.11.7.6\VOLUME1,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp,uid=1000,gid=1000,user=LADIDA,prefixpath=OKAYLINUX-BACKUPS/,pass=********
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
andrea@okaybrain:~$ 
```

Is it normal behaviour to have the mount command trying to mount the path up to volume1 and then do the prefixpath after? The current entry in fstab is 

> //10.11.7.6/volume1/OKAYlinux-backups/

---

### Post by TheFu on 2016-12-13
Please edit the post above and use "code tags".  Can't tell what the real output is and where it is wrapped.

Please add the full, complete, fstab file too. Don't need the exact userid/passwords, but if there are "special characters", and it should, those can impact parsing if not correctly escaped.

Sorry. I don't understand the last question asked. Can you rephrase?

---

### Post by Morbius1 on 2016-12-14
> Is it normal behaviour to have the mount command trying to mount the  path up to volume1 and then do the prefixpath after? The current entry  in fstab is 
Yes ... But ....

The normal way of accessing a shared resource is to specify the server and the shared resource so the syntax would be:
```
//10.11.7.6/VOLUME1
```
Anything past that is considered by CIFS to be the local path within that shared resource so //10.11.7.6/VOLUME1/OKAYlinux-backups will be the OKAYlinux-backups folder within the VOLUME1 share. And it works as advertised if the server is another Linux box or even Windows.

But ... NAS devices in general are really messed up as they all seem to make up their own rules, are designed with Windows in mind, and use antique versions of samba. I would try to mount VOLUME1 then drill down to the OKAYlinux-backups folder once VOLUME1 is mounted.

OR, Mount the folder in case it sees that as the share:
```
 //10.11.7.6/OKAYlinux-backups
```

Should that not work ( which is a distinct possibility ) add another option to your list - nodfs:
> //10.11.7.6/volume1/OKAYlinux-backups/ /mnt/sdd1 cifs username=1,password=2,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp[COLOR=#0000cd]**,nodfs**[/COLOR] 0 0

* [COLOR=#0000cd]**BTW**[/COLOR]: You seem to have some other issues:*
> mount: you didn't specify a filesystem type for /dev/disk/by-uuid/8ae5dcc0-1973-4a12-a177-f756465974b6
You might want to post your entire fstab:
```
 cat /etc/fstab
```
It may be that fstab itself is discombobulated and has nothing to do with what I just posted.

---

### Post by andrea-c on 2016-12-15
> Anything past that is considered by CIFS to be the local path within  that shared resource so //10.11.7.6/VOLUME1/OKAYlinux-backups will be  the OKAYlinux-backups folder within the VOLUME1 share. And it works as  advertised if the server is another Linux box or even Windows.

But ... NAS devices in general are really messed up as they all seem to  make up their own rules, are designed with Windows in mind, and use  antique versions of samba. I would try to mount VOLUME1 then drill down  to the OKAYlinux-backups folder once VOLUME1 is mounted.

So no luck with modifying the mounting path of the synology. Either shortening or adding the nodfs option

I typed "volume1" because that the name of the folder that I can see when ssh into the device but even when trying with uppercase directly in fstab I get this error message

```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```


Here a copy of my fstab. The other error is referring to a partition that appeared one day when making a bootable pen drive of centOS. I think It created a partition and did not manage delete it or reinstall everything from scratch

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d85c136c-c30b-4ef7-9c17-8ffb6fe2951a /boot           ext2    defaults        0       2
/dev/disk/by-uuid/8ae5dcc0-1973-4a12-a177-f756465974b6 /mnt/sda auto nosuid,nodev,nofail,x-gvfs-show 0 0

#UUID=76c46b07-65d8-4be5-aef8-da19ea089487 /mnt/sdb1 ext4 sync,auto,rw,nouser 0 0 
#/dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
#UUID=dc69ebeb-339c-4bd0-9d4a-e0b83ddc825b /mnt/sdc1 ext4 sync,auto,rw,nouser 0 0
#/dev/sdd1 /mnt/sdd1 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0

#Mounting special backup partition for Linux boot drives
//10.11.7.6/volume1/OKAYlinux-backups/ /mnt/sdf1 cifs credentials=/home/LADIDA/LADIDA/LADIDA/LADIDA,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp 0 0

#Mounting the Pegaus for postreSQL backup
//10.11.7.10/Promise\040Pegasus/ /media/share cifs credentials=/home/LADIDA/LADIDA/LADIDA/LADIDA,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmssp 0 0

#/dev/mapper/ubuntu--vg-swap_1 none swap sw,noauto 0 0
```

---

### Post by Morbius1 on 2016-12-15
Don't know. I was going to suggest you ask in the synology forum but that may not help either: [https://forum.synology.com/enu/viewtopic.php?t=102614](https://forum.synology.com/enu/viewtopic.php?t=102614)
> This line in my FSTAB works:-
//192.168.1.12/music /media/dsshare01  cifs  uid=1000,gid=1000,credentials=/home/craig/.dsshare01credentials,iocharset=utf8,[COLOR=#0000cd]**sec=ntlm**[/COLOR]  0 0

But if I create a share where the DSM tells me the mount path is /volume1/test and so change it to:-
//192.168.1.12/volume1/test  /media/dsshare01 cifs  uid=1000,gid=1000,credentials=/home/craig/.dsshare01credentials,iocharset=utf8,sec=ntlm  0 0

I get and error:-
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

In other words, the share doesn't exist.
In my mind if the path is /volume1/test then the share is "test".

** You might want to try the "sec=ntlm" option which sets the security level back to a previous value.

** I don't suppose the following command will tell you exactly what the share name is on that device:
```
smbtree
```

Either that or use NFS. TheFu is our resident expert on all things NFS.

---

### Post by andrea-c on 2016-12-19
> **Morbius1 said:**
> Don't know. I was going to suggest you ask in the synology forum but that may not help either: [https://forum.synology.com/enu/viewtopic.php?t=102614](https://forum.synology.com/enu/viewtopic.php?t=102614)

In my mind if the path is /volume1/test then the share is "test".

** You might want to try the "sec=ntlm" option which sets the security level back to a previous value.

** I don't suppose the following command will tell you exactly what the share name is on that device:
```
smbtree
```

Either that or use NFS. TheFu is our resident expert on all things NFS.

I spoke with their support but no ture answer as when tehy remoted in all were fine on their end. I think is more due to my system to be honest but cannot narrow it down.
I tried with ntlm but no joy and smbtree dosen't print any output from the synology shell.

What does it mean use NFS? mounting it as NFS?

---

### Post by TheFu on 2016-12-19
> **andrea-c said:**
> What does it mean use NFS? mounting it as NFS?

[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)
NFS is the native remote file system for Unix systems. It is how storage is shared across 1 or 10,000 clients.  It is useful for campus/LAN sharing mainly.  Not for use over the internet.  Centralized user/group management is required to be most effective, however.

---

