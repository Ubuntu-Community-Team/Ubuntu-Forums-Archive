---
title: "Saving my failing hard drive"
date: 2009-12-16
forum: Hardware
---

### Post by XrRydr on 2009-12-16
Hi, I have a macbook, I think it's considered 3rd generation, I got it May of 2007.  Today when I tried to boot into it it came up with I/O errors on disk0s2.  I went on my desktop and a quick search says that it's probably a failing hard drive.  I burnt the latest ubuntu live cd and that's where I am now.  When I booted the live cd I had an exclamation mark next to my hard drive saying that it has many bad sectors and should be backed up and replaced.  As a side note, I am pleased that everything works out of the box, even wireless works without problem where I remember I used to have to compile those manually.  

What I'm trying to do now is transfer all of my files onto an external drive.  I can access them through the live cd, the only problem is that it says that I don't have permission to read them.  It's really frustrating to see that my picture folder is right there ready to copy, but it says I don't have permission.  Is there a way around this?

Also, I tried booting up my leopard install cd and went to the disk utility.  I ran the repair function and afterwards said that the disk was ok and appeared bootable, but it's not.  Any ideas?

---

### Post by jm2 on 2009-12-16
Perhaps, the drive you want to copy doesn't have write permissions.

man mount 

mount ... will list the devices load and in (rw, ....) 
the r - read, w - write. If the device you want to write to doesn't have a w. then that could be why  you don't have permission.

---

### Post by alwayshere on 2009-12-16
Clonezilla live cd may help you you should be able to make a copy of your hard drive to another which if ya got a macbook i guess the other drive will have to be external use case holding virgin harddrive. external cases are cheap on ebay 

hope this helps heres the website 

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by XrRydr on 2009-12-17
Let's see, here is the output of "mount" in the terminal:

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/Bob OS type hfsplus (rw,nosuid,nodev,uhelper=devkit)
ubuntu@ubuntu:~$ 

Bob OS is the mac hard drive where I'm trying to get files from.  I can successfully copy some of the files on there, but for some reason the documents, music, pictures, and movies folder have permission problems.  

I downloaded clonezilla and was a little confused at first by the process, I'll read through the website a little more to make sure do it correctly.

---

### Post by jm2 on 2009-12-17
[http://support.apple.com/kb/HT2963](http://support.apple.com/kb/HT2963)
Is an apple link for setting permissions. Perhaps, you have to change them on the apple side?

You can try resetting them from linux, if it will let you. You probably want to be root user or use the sudo command.

On linux side :
man chmod (Changes read/write/execute permissions)
man chgrp (changes group permissions)
man chown (changes ownership permissions)
examples:
before: -rw------ root group file

sudo chmod 666 file
after: -rw-rw-rw root group file

sudo chgrp sys file
after -rw-rw-rw root sys file

sudo chown user file
after: -rw-rw-rw user sys  file

Sorry, I'm not an apple user. Perhaps this might help with the permission issue.

---

### Post by XrRydr on 2009-12-18
Cool thanks.  It turns out I was able to access and copy the files by just using gksudo nautilus.  Sometimes the simplest solutions are easily forgotten.  I've got another question though about hard drive failure.

Would I be ok to just reformat the drive and keep careful backups, or would I be better off to just buy a new hard drive to replace it?

---

