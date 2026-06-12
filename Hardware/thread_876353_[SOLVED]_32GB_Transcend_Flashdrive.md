---
title: "[SOLVED] 32GB Transcend Flashdrive"
date: 2008-07-31
forum: Hardware
---

### Post by finito on 2008-07-31
I got this as soon as I laid my eyes on it. I got it when I was traveling  so I mainly used it on Windows. Today I come to my Ubuntu box to give it whirl. and it shows up as a Read-only system. I even tried using sudo commands to cp and mv all that crap. I also tried to chown. it just keeps coming up as Read-only file system. I tried it on VMware WinXP and it works perfectly. Does this mean it uses a new type of file system that is not understandable by Linux.....

---

### Post by jualin on 2008-07-31
Very nice how much?

---

### Post by finito on 2008-07-31
about 120 USD. can anyone help me make this work

---

### Post by ibuclaw on 2008-07-31
With the drive inserted and mounted, what does:
```
cat /etc/mtab
```
tell you?

Regards
Iain

---

### Post by finito on 2008-07-31
well I have 3 HDs the Flash drive is called FINITO ubuntu doesnt like the drive so it mounts it again everytime 

```
/dev/sdb2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdc1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sda1 /media/disk-1 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdd1 /media/FINITO___ vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sde1 /media/FINITO____ vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdf1 /media/FINITO_____ vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

FINITO_____ is the one that was mounted right now...

---

### Post by ibuclaw on 2008-07-31
lol, that is very interesting, I would imagine that it would be no different, it's just a regular fat32, isn't it? Did you need to install any drivers on windows to get it working?

---

### Post by finito on 2008-07-31
nope just regular plug and play

---

### Post by finito on 2008-08-01
bump

---

### Post by jualin on 2008-08-01
When I first saw your thread I though it was in the "Community Cafe Discussions" area. Sorry I have no idea of a solution for your problem. I also thought that since is plug and play in Windows it should have a common file system that Ubuntu could pick up. Sorry!

---

### Post by finito on 2008-08-01
I tried it on a few ubuntu machines none of them like the flash drive I don't get it.. it is getting annoying

---

### Post by finito on 2008-08-02
I would really appreciate if someone knew why this isnt working

---

### Post by jualin on 2008-08-02
I have been looking for a solution for your problem but google hasn't found anything yet. Maybe since not too many people have bought these new gadgets the problem hasn't become widesread yet. I will keep on looking for a solution. Good luck!

---

### Post by firefeather on 2008-08-02
Just a thought: That drive doesn't happen to be one of those fancy U3 drives, does it? (When you plug it in to windows, does it run a U3 interface?)

---

### Post by jualin on 2008-08-02
I don't think that having that interface makes a difference. I have a Lexar Flash drive with the U3 interface but it runs perfectly in Ubuntu (withouth the U3 interface)

---

### Post by silkstone on 2008-08-02
Sometimes these flash drives actually have two partitions that are read as a floppy drive and FAT32. The floppy part has encryption for password support. I'm not sure how Linux handles that.

Have you looked at the drive with gparted to see if anything else is there?

EDIT/ And if all else fails, have you tried formatting it with gparted?

---

### Post by jualin on 2008-08-02
can you check the filesystem using Gparted? Maybe you need to format it to NTFS. If you don't have it installed already you can install it via terminal > sudo apt-get install gparted or via Synaptic Package Manager. Just a shot in the dark.

---

### Post by jualin on 2008-08-02
[This is the thread ]("http://ubuntuforums.org/showthread.php?t=591854") that I got the idea from. It also suggests disabling the password in Windows and then trying to use it in Ubuntu. Just like silkstone suggested as well.

---

### Post by finito on 2008-08-02
There is no Password.
I will try to reformat but these things are slow so it may take a few hour i will let you know how it goes

---

### Post by jualin on 2008-08-02
Ok, I will be here for the next two hours so let me know.

---

### Post by finito on 2008-08-02
This is rather strange. in Gparted it shows 4mb unallocated. I just deleted all the partitions and formatted it to fat32 and it seems to be working. 

rather strange. I will let it back everything up and try to remount and see.

above all that formatted rather quick.

---

### Post by jualin on 2008-08-02
tell me how it all goes when everything is gone. I would love to get one of those flash drives for myself and use it in Ubuntu. 32 GB is a lot of memory for a Flash drive.

---

### Post by finito on 2008-08-02
Hmm it works.

that is very silly. When I deleted 4mb of unallocated space the disk got faster and I gained 40mb of space.

---

### Post by jualin on 2008-08-02
Nice, I am very glad to hear it worked!! Enjoy your flash drive.):P

---

### Post by silkstone on 2008-08-02
That makes sense! The reformat should have been quick - just a few seconds for a quick format. You had a flash drive with a hidden partition intended for password protection, and now that has gone and you have a fully usable drive. It should work fine in both Linux and Windows now.

---

