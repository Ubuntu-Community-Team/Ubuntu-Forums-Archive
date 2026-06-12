---
title: "Get dpkgs from a different partition"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by callistino on 2009-09-28
Hi guys, I'm having a little bit of trouble finding a way to get the packages from a different partition. Here is what happened:

I was playing with the fstab file and broke my installation (Wubi installation on Vista). I couldn't fix the file because I did not have the permissions to do it. When I tried to boot onto recovery mode the X server wouldn't start and I was dropped to a shell. I tried to fix the file there but got permissions errors even using sudo. 

I made a new space in the drive and did a fresh install (from CD this time). Now I am looking for a way to get my dpkgs from the old installation. I can mount the old disks and I am able to browse all the odl files but can't use the dpkg commands to get the intalled packages because they are not the current filesystem. I already copied my home folder but I am looking to get the old programs and settings. Is there a way to do this?

Please let me know what can I do. Thanks.

---

### Post by unutbu on 2009-09-28
Suppose you mount your old installation at /OS2.
Then try
```

cd /OS2
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /OS2
```

This (if successful) will give you a root shell as though you had booted into the old installation.

Now install the dpkg-repack and fakeroot packages on your old installation:
```

sudo apt-get install dpkg-repack fakeroot
```

Make a directory in which to place the debs you are about to create:
```

mkdir /root/deb-archives; cd /root/deb-archives
```Note that your new installation will see this directory as /OS2/root/deb-archives.

Repackage your software into debs. For example:
```

fakeroot -u dpkg-repack gparted graphviz apt-rdepends python-pygame wesnoth-all testdisk ipython gphoto2 python-gtk2-doc python-matplotlib-doc inkscape python-rpy python-rpy-doc conky

```
Then in a new terminal: (so you are not in the chroot environment)```

cd /OS2/root/deb-archives
sudo dpkg -i *.deb        # This will install all the debs on to your new installation

```
Note that this will not solve dependency problems for you. If you find you are having dependency problems, I have a python script which might help, but first let's see if the above moves you a few yards before we go for the touchdown.

PS. If you have enough space in /OS2, you could simply repack all the packages. That would be a simple way to avoid dependency problems. The command to do this would be
```

fakeroot -u dpkg-repack $(aptitude -F '%?p' search '~i')
```

---

### Post by callistino on 2009-09-28
Thanks for the fast response.

I tried you first set of code and got this:
chroot: cannot run command `/bin/bash': Exec format error

This is exactly what I wanted but it is not working. Is there any problem with my shell?
I am running the same 64 bit version of Ubuntu 9.04. Do you think that by having to mount the vista drive first (NTFS) and then the wubi root (ext3), could be causing it to think it is not a ext3 partition?
Should I copy the old filesystem from inside the Vista drive to the new partition and that way it would'nt have to get it through an ntfs partition?

---

### Post by unutbu on 2009-09-28
Hm. I'm not quite sure. Could you please post the output of 
```

mount
```

---

### Post by callistino on 2009-09-28
I took a while to reply because I was trying your code from the live-CD. This is the output of mount from it. I f you need me to do it from the installation let me know.

```

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/TOSHIBA EXT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/WindowsXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/loop1 on /media/root.disk type ext3 (rw)
/proc on /media/root.disk/proc type none (rw,bind)
/sys on /media/root.disk/sys type none (rw,bind)
/dev on /media/root.disk/dev type none (rw,bind)
ubuntu@ubuntu:~$ 
```

---

### Post by unutbu on 2009-09-28
Still not sure what the problem is. Please post the output of 
```

ls -l /bin/bash
file /media/root.disk/bin/bash
```

---

### Post by callistino on 2009-09-28
Ok here it is: 

```

ubuntu@ubuntu:~$ ls -l /bin/bash
-rwxr-xr-x 1 root root 729040 2009-03-02 14:22 /bin/bash
ubuntu@ubuntu:~$ file /media/root.disk/bin/bash
/media/root.disk/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
ubuntu@ubuntu:~$ 

```

---

### Post by unutbu on 2009-09-28
Are you mounting the wubi filesystem with
```

sudo mount -t ntfs-3g /dev/sdXY /media/WindowsXP
sudo mount -o loop /media/WindowsXP/wubi/disks/system.virtual.disk /media/root.disk
```

If not, how are you mounting it?

PS. Since what I described works for non-Wubi installations, and since I have zero experience with Wubi, I'm afraid there might be some issue related to Wubi-ness that I'm not aware of.

---

### Post by callistino on 2009-09-28
I am using a script that was posted on 

[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

There is something bothering me. Why is it listed as /media/WindowsXP? My Windows is Vista not XP. Well I will try mounting like you said in the last post ans see if it solves the problem.

---

### Post by unutbu on 2009-09-28
> **callistino said:**
> 
Should I copy the old filesystem from inside the Vista drive to the new partition and that way it would'nt have to get it through an ntfs partition?

This might work, but I'm not 100% sure.

---

### Post by callistino on 2009-09-29
I found what the problem was. I used the file command on the live cd bash file and i came as the 32 bit version ( I could have swear otherwise) So I will try burning a 64 bit version now for sure and go from your first post adn see what happens. Thanks for anything. Will let you know if I succed.

---

