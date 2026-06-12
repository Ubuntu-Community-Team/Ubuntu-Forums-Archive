---
title: "Unable to unmount or delete a useless image."
date: 2008-10-29
forum: General Help
---

### Post by DanTheFlyingMan on 2008-10-29
A friend was trying to install Worms Armageddon on my laptop. He wasn't successful, and now there is something mounted (I think it is an image of the Worms disk) that I can't unmount or delete. When I try to unmount the file I get:

> Unable to unmount mountpoint

umount: /home/daniel/Programs/Play Worms Armageddon on linux/play_WA_on_linux/mountpoint is not in the fstab (and you are not root)

Trying to unmount it as root doesn't work because it isn't mounted as root. When I try to delete it as root I get:

> Error while deleting

There was an error deleting mountpoint.

Error removing file: Device or resource busy

I have no idea what to do. Any ideas?

---

### Post by Darkade on 2008-10-29
try running
    # fuser -m /media/mountpoint

For more info check it [here]("http://www.google.com/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Focaoimh.ie%2F2008%2F02%2F13%2Fhow-to-umount-when-the-device-is-busy%2F&ei=ie4HSY-8IYzgML2otO8G&usg=AFQjCNFkjEseSRYeUP0VRWifOxt4a_Fu6A&sig2=sCFhCkKCfl0w852tDkboGQ"): 

hope it works

---

### Post by ryanhaigh on 2008-10-29
> Error removing file: Device or resource busy
Indicates that something is still accessing the files or perhaps you have a terminal open where the current directory is part of the image.

What is the output of the command
```
mount
```

---

### Post by Darkade on 2008-10-29
Also this weeks tutorial of the week :P is about that

[http://ubuntuforums.org/member.php?u=352493](http://ubuntuforums.org/member.php?u=352493)

**EDIT:** Sorry wrong link
this is the one [http://ubuntuforums.org/showthread.php?t=704350](http://ubuntuforums.org/showthread.php?t=704350)

---

### Post by DanTheFlyingMan on 2008-10-29
> **Darkade said:**
> try running
    # fuser -m /media/mountpoint

For more info check it [here]("http://www.google.com/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Focaoimh.ie%2F2008%2F02%2F13%2Fhow-to-umount-when-the-device-is-busy%2F&ei=ie4HSY-8IYzgML2otO8G&usg=AFQjCNFkjEseSRYeUP0VRWifOxt4a_Fu6A&sig2=sCFhCkKCfl0w852tDkboGQ"): 

hope it works

That didn't do anything. :(

> **ryanhaigh said:**
> Indicates that something is still accessing the files or perhaps you have a terminal open where the current directory is part of the image.

What is the output of the command
```
mount
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/loop0 on /home/daniel/Programs/Play Worms Armageddon on linux/play_WA_on_linux/mountpoint type iso9660 (rw)
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)

Thanks for the fast replies!

---

### Post by ryanhaigh on 2008-10-29
What happens if you try:
```
sudo umount -d /dev/loop0
```
There is also a force option:
```
sudo umount -f /dev/loop0
```

[http://linux.die.net/man/8/umount](http://linux.die.net/man/8/umount)

You might also be able to use lsof to determine if any files from the mounted loop device are currently open. [http://www.linux.com/articles/114089](http://www.linux.com/articles/114089)

---

### Post by DanTheFlyingMan on 2008-10-29
> **ryanhaigh said:**
> What happens if you try:
```
sudo umount -d /dev/loop0
```
There is also a force option:
```
sudo umount -f /dev/loop0
```

[http://linux.die.net/man/8/umount](http://linux.die.net/man/8/umount)

You might also be able to use lsof to determine if any files from the mounted loop device are currently open. [http://www.linux.com/articles/114089](http://www.linux.com/articles/114089)

daniel@5720z:~$ sudo umount -d /dev/loop0
[sudo] password for daniel: 
ioctl: LOOP_CLR_FD: No such device or address
daniel@5720z:~$ sudo umount -f /dev/loop0
umount2: Invalid argument
umount: /dev/loop0: not mounted

I'll have a look at the links a little later, I've got to go out now.

Edit: Wait, that seems to have done it! Thank you!

---

