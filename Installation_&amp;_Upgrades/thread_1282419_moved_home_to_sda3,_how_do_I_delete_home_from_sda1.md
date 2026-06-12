---
title: "moved /home to sda3, how do I delete /home from sda1?"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by newboyo on 2009-10-04
Hello,


[LIST]
[*]I split my hard drive into sda1 (~55 GB) and sda3 (~ 260 GB).
[*]copied /home from sda1 to sda3.
[*]amended fstab to load home from sda1.
[/LIST]
I'd like to delete /home from sda1, but am unsure of how to check that /home from sda1 is not being used, prior to deleting it.

Any help will be appreciated.

Thanks 

New

---

### Post by Lars Noodén on 2009-10-04
What is the output from [FONT="Courier New"]mount[/FONT]?  

That should show you which devices the mount points are using.  

It should say something like this:

[FONT="Courier New"]/dev/sda3 on /home type ext3 (rw)[/FONT]

---

### Post by newboyo on 2009-10-04
Thanks for your message. Here's the result -


/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/newboyo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=newboyo)


Does this mean that /home on sda1 can be deleted?

---

### Post by slakkie on 2009-10-04
> **newboyo said:**
> 
Does this mean that /home on sda1 can be deleted?


The contents of /home can be removed, but you can't remove the dir, since it will be used for mounting.

---

### Post by newboyo on 2009-10-04
> **slakkie said:**
> The contents of /home can be removed, but you can't remove the dir, since it will be used for mounting.


I'm afraid I didn't understand this. Won't the /home from sda3 be used for mounting?

---

### Post by Lars Noodén on 2009-10-05
> **newboyo said:**
> Thanks for your message. Here's the result -
/dev/sda1 on **/** type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on **/home** type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/newboyo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=newboyo)


Does this mean that /home on sda1 can be deleted?

From here it looks like you are using it.  Before you delete it, try unmounting it.  

[FONT="Courier New"]sudo umount /dev/sda3[/FONT]

If that doesn't give errors or trouble then try commenting it out of /etc/fstab and rebooting (just to kill / unmount everything to be sure).  
That can be done by adding a pound sign (#) at the very beginning of the line in /etc/fstab that mentions /dev/sda3.

If you still are OK, then you can consider deleting it (sda3).

---

### Post by Lars Noodén on 2009-10-05
> **newboyo said:**
> I'm afraid I didn't understand this. Won't the /home from sda3 be used for mounting?

Right idea but it's the other way around.  According to the output you posted, /home on /dev/sda1 is where /dev/sda3 is attached.

---

### Post by slakkie on 2009-10-05
> **newboyo said:**
> I'm afraid I didn't understand this. Won't the /home from sda3 be used for mounting?

You need to keep the directory /home on sda1 because it will be used as a mountpoint for the mount of sda3. If you remove /home on sda1 it cannot mount sda3 as /home.

You can remove all the files within /home on sda1, but not the dir /home. 

```

umount /home
rm -rf /home/*
mount /home

```

Although I would boot from some liveCD and mount sda1 and then remove the contents of /home. Since running Gnome/KDE sessions will keep /home busy so umounting could become troublesome on a running system.

As root on when running of a liveCD:

```

mkdir -p /mnt/root
mount /dev/sda1 /mnt/root
rm -rf /mnt/root/home/*
umount /mnt/root
reboot

```

---

### Post by renkinjutsu on 2009-10-05
No need..

you can just mount /dev/sda1 in two locations

```
sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/home/*
sudo umount /mnt
```

---

### Post by Lars Noodén on 2009-10-06
> **renkinjutsu said:**
> No need..

you can just mount /dev/sda1 in two locations

```
sudo mount /dev/sda1 /mnt
sudo rm -r /mnt/home/*
sudo umount /mnt
```

@renkinjutsu: Thanks.  That was clever.

---

### Post by newboyo on 2009-10-07
Thank you all. I deleted stuff from /home on sda1, but did not delete /home. will try the other methods later.


rgds newboyo

---

