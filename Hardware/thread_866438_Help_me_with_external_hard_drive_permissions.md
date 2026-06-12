---
title: "Help me with external hard drive permissions?"
date: 2008-07-21
forum: Hardware
---

### Post by i_animal_machine on 2008-07-21
Hi, I am relatively new to ubuntu. I have an external hard drive, a Maxtor Onetouch 750 Gig, that I have in 2 partitions, one for windows storage, and the other for ubuntu storage. The Ubuntu partition is ntfs filesystem, and for this thread I'll just call it "Ubuntu Storage". When I attempt to access it in Ubuntu, it tells me that I don't have the permissions to use it. I have no idea how to change these permissions..

Any suggestions?????

---

### Post by i_animal_machine on 2008-07-22
Bump.. Please help. Do i use fstab??

---

### Post by vanadium on 2008-07-22
Is it correct that the "Ubuntu partition" is ntfs? ntfs is the Windows file system. You probably mean ext3.

From the output of the command "mount", determine the mount point of the drive. Then change the owner of the mount point to yourself as a user. If you post the output of "mount" here, we can give you the correct command.

Alternatively, if multiple users are to use the drive, leave the permissions of the mount point as is. Instead, create directories for each of the users, and change the owner to the respective users.

---

### Post by bahg526 on 2008-07-22
I've encountered the same issue with my maxtor onetouch 500. I used gparted to format it from ntsf to ext3. But I have no permissions to write. 

> name@box:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/loot type ext3 (rw,nosuid,nodev,uhelper=hal)


The device is /dev/sdb1 on /media/loot.

How do I fix this?

---

### Post by freakalad on 2008-07-22
I'm presently having problems along similar lines.

Have 750 GB Maxtor external, NTFS.
Have a 750 GB Lasie NAS.

ntfs-3f, cifs, smbfs, samba & the rest installed.

I have 2 shares ready, with chmod 744 & chown me:users (id's 1000:100).

Been able to execute the following:
mount -t ntfs-3g /dev/disk/by-uuid/007C964A77FD9E3E /media/kool/
Mounts OK, but sets the permissions to: 777 root:root

Able to execute the following:
sudo mount -t smbfs //10.0.0.10/media /media/lacie_media
Mounts & sets permissions the same, but I'm unable to write to the share (but that may be due to a network rights issue).

I need help tweaking my /etc/fstab enties.

Want my original permissions of 744 me:users on my mounts. 
 
Got this far:

UUID=007C964A77FD9E3E    /media/kool    ntfs-3g defaults=rw,exec,user,auto,user_id=1000,group_id=100,dir_mode=0744,file_mode=0750   0 0
//10.0.0.10/media /media/lacie_media    smbfs   defaults=rw,exec,user,auto,user_id=1000,group_id=100,dir_mode=0744,file_mode=0750   0 0

Any user/process must be able to automatically mount any drive, but a hard mount must me skipped @ boot, to prevent undue long boot if drive/resource is not present.

Losing the plot with some of the new arguments.
Also, what are the significant difference in arguments when applying different protocols? Have nfs, hpfs & vfat/fat32 shares I want to mount too.

Can somebody refer me to a concise resource?

Please help

---

### Post by Daelyn on 2008-07-22
I had the same problem with my external drive, which is NTFS.

I just did a 
```
chmod 777 -R /{the mount point} 
``` 
and haven't had any issues since. Works flawless on my mates windoze machine and have been working for a year on my ubuntu laptop without any problems.

Maybe it's the wrong way to do it, but, I was a linux n00b back then.

---

### Post by bahg526 on 2008-07-22
> **Daelyn said:**
> I had the same problem with my external drive, which is NTFS.

I just did a 
```
chmod 777 -R /{the mount point} 
``` 
and haven't had any issues since. Works flawless on my mates windoze machine and have been working for a year on my ubuntu laptop without any problems.

Maybe it's the wrong way to do it, but, I was a linux n00b back then.

When I try that I get this msg:

[CODE]chmod 777 -R /media/drv
chmod: changing permissions of `/media/drv': Operation not permitted
chmod: changing permissions of `/media/drv/lost+found': Operation not permitted
chmod: cannot read directory `/media/drv/lost+found': Permission denied

---

### Post by tonyh6243 on 2008-07-22
It may go without saying but make sure you are running this with the sudo command.

---

### Post by freakalad on 2008-07-22
777 should be OK for a n00b, as this is a quick dirty but effective way of cutting through all the BS, but it's a REALLY bad idea in the long run, as this opens you drive up to all sorts of nasties. I occasionally resort to it myself.

I'd SUPER cautious using the following characters (regardless of what comes after the "/"):
sudo chmod -R 777 /
Would so a number on your system, nearly as bad as:
sudo rm -R /

But I also have a hard time getting my head around some of the permissions, fstab arguments & other FS stuff, and I've been at it for year. I've also seen some implementations change between distro's & version, so don't feel bad if you can't nail it down

---

### Post by Daelyn on 2008-07-22
> **freakalad said:**
> 777 should be OK for a n00b, as this is a quick dirty but effective way of cutting through all the BS, but it's a REALLY bad idea in the long run, as this opens you drive up to all sorts of nasties. I occasionally resort to it myself.

I'd SUPER cautious using the following characters (regardless of what comes after the "/"):
sudo chmod -R 777 /
Would so a number on your system, nearly as bad as:
sudo rm -R /

But I also have a hard time getting my head around some of the permissions, fstab arguments & other FS stuff, and I've been at it for year. I've also seen some implementations change between distro's & version, so don't feel bad if you can't nail it down

Well. It is a external HDD, and a NTFS partition is "free for all" in it's basic formatting anyways. Windoze won't give a damn if he plugs it in :)

It is all down to his own preference of course :)

---

### Post by freakalad on 2008-07-22
true. true

I've set mine up as a dump for torrentflux dl's, so I'm a bit cautious of giving any process or user RWX abilities (W or X; not both)

could you please have a look o@ my query up above & point me to a good reference? (even outside of UF)

---

### Post by freakalad on 2008-07-25
is this thread now dead?

will repost my request & remove these last blips after the weekend if I don't find a solution

---

### Post by big_wanda on 2008-08-08
I am having the same problem, but I don't have a clue as to what you are telling to perform.  As far as the code, I understand that is in a terminal, but do I just enter exactly what you suggest or are there things that I must know and tailor for my system?  If so, could you please include them?  

I am so new at this, I am not even sure what info I need to provide to this thread so as to not waist anyones time.  :(  What is chom?
thanks for the help.

---

### Post by freakalad on 2008-08-10
hey big_wanda,

no worries.
depend on what you're referring to.

permissions is one of the most important & trickiest subject in linux to get your head around, in it's entirety. i still have trouble with it several years down the line
it's important to distinguish simple permissions vs. ownership.
chmod & chown are used to alter ownership, permissions & rights on objects (files, directories, etc), but it's easy to lock yourself out or give even the most casual user full access to do whatever they wish on your system (ridiculously stupid thing to do, but happens incredibly easy). 
to complicate matters more, umask uses the compliment/mirror of these properties.

you best bet to get a grip on right & permissions would be:
1. man pages. type in "man" followed bay a command to get the help; otherwise the command followed by "--help". this is often referred to as RTFM (not meant in a disparaging way, but is an acronym for "Read The Friggin' Manual"). This is standard user lexicon, so don't feel offended is someone 'points' this term at you
2. users forums such as this are EXCELLENT sources for information. you just have to ask the right question in the right are & you should get a speedy response
3. google

i hope this points you in the right direction.
good luck & i wish you smooth sailing. 
keep hope; you'll get there

---

